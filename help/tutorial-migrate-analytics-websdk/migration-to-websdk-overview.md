---
title: Migrieren von Adobe Analytics zu Web SDK mithilfe von Tags
description: Erfahren Sie mehr über die Schritte, die Sie während der Migration zu Web SDK durchführen werden, sowie über die Entscheidungen, die während des Migrationsprozesses getroffen werden müssen.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16755
exl-id: e578b669-42b4-46ae-b6e6-6688e5c5c772
source-git-commit: d6471c8e383e22fed4ad5870952d0d0470f593db
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# Migrieren von Adobe Analytics zu Web SDK mithilfe von Tags

Erfahren Sie, wie Sie eine Adobe Analytics-Implementierung mithilfe der Analytics-Erweiterung in Experience Platform-Tags (ehemals Launch) zu Web SDK migrieren, indem Sie die Web SDK-Erweiterung auch in Tags verwenden. Wenn die Adobe Analytics-Erweiterung in Tags verwendet wird, wird hinter den Kulissen der Code &quot;AppMeasurement.js“ verwendet. Daher können Sie sich dieses Tutorial als ein Tutorial vorstellen, das AppMeasurement zu Web SDK migriert. Dieses Tutorial befindet sich jedoch vollständig in Tags und behandelt NICHT den Wechsel zu oder von einer JavaScript-Implementierung (mit Ausnahme von JavaScript-Code, der in der Tags-Benutzeroberfläche verwendet wird). Informationen zur Migration von JavaScript-Implementierungen finden Sie in der [Dokumentation](https://experienceleague.adobe.com/de/docs/analytics/implementation/aep-edge/web-sdk/appmeasurement-to-web-sdk).

>[!NOTE]
>
>Ähnliche Migrations-Tutorials sind verfügbar für:
>
> * [Adobe Target](../tutorial-migrate-target-websdk/introduction.md)
> * [Adobe Audience Manager](https://experienceleague.adobe.com/de/docs/audience-manager/user-guide/migrate-to-web-sdk/appmeasurement-to-web-sdk)

>[!CAUTION]
>
> Da Platform Web SDK mehrere Adobe-Anwendungen unterstützt, sollten alle Adobe-Bibliotheken auf einer bestimmten Seite gleichzeitig migriert werden. Beispielsweise wird eine gemischte Implementierung von Web SDK for Target und AppMeasurement for Analytics auf einer Einzelseite _nicht unterstützt_. Es wird jedoch eine gemischte Implementierung über verschiedene Seiten hinweg unterstützt, z. B. Web SDK auf Seite A und at.js mit AppMeasurement auf Seite B.

## Was Sie aus diesem Tutorial erhalten

Bevor wir mit den Schritten zur Migration Ihrer Analytics-Implementierung beginnen, ist es wichtig, dass Sie genau verstehen, was Sie tun werden, nämlich die _Implementierung“_ Analytics ändern/aktualisieren. Wenn Sie am Ende dieses Tutorials in Ihre Berichte eingehen und alles gleich ist, fragen Sie sich vielleicht: „Warum habe ich das alles getan?“ Es gibt weitere Dokumente, in denen die Vorteile der Verwendung von Web SDK für Ihre Analytics-Implementierung beschrieben werden, aber einige sind:

1. Unterstützung für First-Party-Geräte-ID
1. Bessere Leistung
1. Zukünftiges Proofing Ihrer Implementierung auf dem Weg zur Verwendung der Adobe Experience Platform-Programme (Ermöglichen neuer Anwendungsfälle)

Wenden Sie sich an Ihren Adobe Analytics-Support-Mitarbeiter, um mehr darüber zu erfahren, wie Ihnen Web SDK helfen kann. Während wir mit diesem Tutorial fortfahren, konzentrieren wir uns auf _wie_ die Migration durchzuführen.

>[!IMPORTANT]
>
>Beachten Sie, dass einer der Hauptgründe für diese Migration Ihrer Implementierung die Vorbereitung auf die Verwendung von Adobe Experience Platform-Programmen wie Customer Journey Analytics, Real-Time CDP oder Journey Optimizer ist (wie oben #3). Die Verwendung Ihrer Website-Daten zu diesem Zweck umfasst zusätzliche Schritte, die in diesem Tutorial nicht enthalten sind, aber dieses Tutorial ist sicherlich eine Voraussetzung für diesen weiteren Fortschritt Ihrer Implementierung. Schließen Sie daher dieses Tutorial ab, und führen Sie dann die Schritte aus, die erforderlich sind, um dieselben Website-Daten auch an die Experience Platform zu senden.

## Migrationsmethode

Es gibt wahrscheinlich viele Möglichkeiten für diesen Migrationsprozess, aber wir müssen genau hier über zwei sprechen:

**Methode 1:** Aktualisieren Sie Ihre bestehende Tags-Eigenschaft auf Web SDK, erstellen Sie neue Datenelemente und nehmen Sie Änderungen an den Regeln vor, die bereits in Ihrer Eigenschaft vorhanden sind.

**Methode 2:** Sie können auch eine neue Eigenschaft erstellen (indem Sie die vorhandene kopieren oder eine brandneue Eigenschaft erstellen) und diese neue Eigenschaft dann mit Web SDK anstelle der Adobe Analytics-Erweiterung konfigurieren.

**Für dieses Migrations-Tutorial verwenden wir Methode 1.** sind die mit der Eigenschaft verknüpften Einbettungs-Codes bereits auf Ihren Entwicklungs-, Staging- und Produktions-Sites eingebettet, sodass Sie keine Einbettungs-Codes ändern müssen. Wenn Sie sich für Methode 2 entscheiden, vergessen Sie nicht, die neuen Einbettungs-Codes für jede Umgebung aus dem Abschnitt **Umgebungen** der neuen Eigenschaft abzurufen und sie in den Head-Abschnitt Ihrer Site einzufügen.

>[!NOTE]
>
>Auch wenn wir während dieser Migration einfach unsere vorhandene Eigenschaft in Tags bearbeiten, ist es dennoch eine gute Idee, vorsichtig zu sein. Daher wird dringend empfohlen, eine Kopie Ihrer aktuellen Eigenschaft zu erstellen, bevor Sie mit der Migration beginnen. Auf diese Weise konnte man immer in die Kopie gehen und sehen, wie die Dinge waren, bevor man sie änderte, Code daraus abrufen, etc.
>Es ist nur gut, vorsichtig zu sein, nur für den Fall. Erstellen Sie die Kopie Ihrer Eigenschaft. Ich warte hier, bis du zurückkommst.

## Schritte für die Migration Ihrer Analytics-Implementierung zu Web SDK

Wenn man die einzelnen Schritte durchläuft, gibt es einige Einschränkungen, die unbedingt zu verstehen sind:

1. Erstens benötigen Sie möglicherweise nicht alle diese Schritte. Es gibt zum Beispiel eine Lektion über das Migrieren von benutzerdefiniertem Code. Wenn Sie über eine Tags-Implementierung verfügen, die keinen benutzerdefinierten Code verwendet (einschließlich der Verwendung von Plug-ins), benötigen Sie diese Lektion nicht. Wir haben versucht, die Lektionen einzubeziehen, die von den meisten Menschen benötigt würden. Lesen Sie daher zumindest die Lektionen, um zu sehen, ob Sie während Ihrer Migration Anpassungen an Ihrer Site vornehmen müssen.
1. Außerdem gibt es einfach keine Möglichkeit für uns, ein Migrations-Tutorial zu erstellen, das 100 % der Anwendungsfälle abdeckt, die jeder verwendet. Wie im vorherigen Punkt erwähnt, haben wir versucht, die Lektionen einzubeziehen, die die meisten Menschen benötigen und die die meisten der wichtigsten Anwendungsfälle abdecken werden. Es wird jedoch zweifellos Anwendungsfälle geben, die in diesem Tutorial nicht behandelt werden. In diesem Fall sollten Sie überprüfen, ob die enthaltenen Lektionen Ihnen eine gute Vorstellung davon vermitteln, wie Sie für Ihren Anwendungsfall migrieren sollten. Sie können auch Ihre Kollegen in der [Experience League-Community um eine Datenerfassung bitten](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/ct-p/adobe-launch-community?profile.language=de).

Der Migrationsprozess umfasst die folgenden wichtigen Schritte:

1. Erstellen Sie eine Report Suite für die Migrationsvalidierung.
1. Erstellen und Konfigurieren eines Datenstroms.
1. Fügen Sie die Web SDK-Erweiterung in Tags (ehemals Adobe Launch) hinzu und konfigurieren Sie sie.
1. Erstellen Sie ein neues Datenelement, um Daten über die Web-SDK an zu senden.
1. Migrieren Sie Ihre standardmäßige Seitenladeregel, um das Datenelement und die Aktionen von Web SDK zu verwenden.
1. Migrieren von benutzerdefiniertem Code in Regeln oder für Plug-ins.
1. Publish - Ihre Implementierungsänderungen.
1. Erfahren Sie, wie Sie Ihre Änderungen debuggen und validieren und Ihre standardmäßige Seitenladeregel und die damit verbundenen Variablen validieren. Diese Validierung sollte dann während der gesamten Migration fortgesetzt werden, wenn Sie Änderungen vornehmen.
1. Migrieren Sie zusätzliche Seitenladeregeln.
1. Migrieren von Regeln für benutzerdefinierte Links.
1. Entfernen Sie nach der vollständigen Validierung Verweise auf die Analytics-Erweiterung und entfernen Sie die Erweiterung selbst.
1. Nachdem Sie alle Änderungen vorgenommen haben, übertragen Sie die Bibliothek in die Staging-Umgebung und dann in die Produktion.
1. Wenn alles abgeschlossen ist, testen Sie es erneut. Dies ist notwendig, da Sie Änderungen vorgenommen haben, indem Sie die Verweise auf den alten Analytics-Code entfernt haben, und Sie sicherstellen möchten, dass alles weiterhin korrekt funktioniert.

>[!NOTE]
>
>Wir möchten Sie bei der erfolgreichen Migration von Analytics zu Web SDK unterstützen. Wenn Sie auf Hindernisse bei Ihrer Migration stoßen oder das Gefühl haben, dass wichtige Informationen in diesem Handbuch fehlen, lassen Sie es uns bitte wissen, indem Sie in [diese Community-Diskussion](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-analytics-to-web-sdk-using/m-p/732308?profile.language=de#M604){target="_blank"} posten.

