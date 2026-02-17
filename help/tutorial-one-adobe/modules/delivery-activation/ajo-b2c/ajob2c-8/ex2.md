---
title: Erstellen einer orchestrierten Kampagne
description: Erstellen einer orchestrierten Kampagne
kt: 5342
doc-type: tutorial
exl-id: f3ca3230-db30-4e41-91f1-9324b12211a6
source-git-commit: 53be5cf34db144e346f9810359b583072743382f
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 2%

---

# 3.8.2 Erstellen einer orchestrierten Kampagne

## 3.8.2.1 Erstellen einer orchestrierten Kampagne

Navigieren Sie zu **Kampagnen**. Klicken Sie **Kampagne erstellen**.

![AJO OC](./images/ajooc1.png)

Wählen Sie **Orchestrierung - Marketing** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc2.png)

Geben Sie den Kampagnennamen ein: `--aepUserLdap-- - CitiSignal Family Account Optimization Campaign` und klicken Sie auf **Speichern**.

![AJO OC](./images/ajooc3.png)

Sie sollten das dann sehen. Klicken Sie auf das Symbol **+**.

![AJO OC](./images/ajooc4.png)

Wählen Sie **Verzweigung** aus.

![AJO OC](./images/ajooc5.png)

### Zielgruppe 1 erstellen

Klicken Sie auf das Symbol **+** und wählen Sie **Zielgruppe erstellen** aus.

![AJO OC](./images/ajooc6.png)

Klicken Sie, um den Ordner für &quot;**&quot;** öffnen.

![AJO OC](./images/ajooc7.png)

Wählen Sie **`--aepUserLdap--_citisignal_recipients`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc8.png)

Klicken Sie **Zielgruppe erstellen**.

![AJO OC](./images/ajooc9.png)

Klicken Sie **Bedingung hinzufügen**.

![AJO OC](./images/ajooc10.png)

Wählen Sie **recipient_type** aus und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc11.png)

Geben Sie **`account_holder`** in das Feld **Wert** ein und klicken Sie auf **Berechnen**.

![AJO OC](./images/ajooc12.png)

Anschließend sollte eine Zahl für &quot;**&quot; angezeigt**. Klicken Sie wie angegeben in den grauen Bereich.

![AJO OC](./images/ajooc13.png)

Klicken Sie **Bedingung hinzufügen**.

![AJO OC](./images/ajooc14.png)

Drilldown nach **`citisignal_accounts`**.

![AJO OC](./images/ajooc15.png)

Wählen Sie **`account_status`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc16.png)

Geben Sie **`active`** in das Feld **Wert** ein. Klicken Sie dann wie angegeben in den grauen Bereich.

![AJO OC](./images/ajooc17.png)

Klicken Sie **Bedingung hinzufügen**.

![AJO OC](./images/ajooc18.png)

Drilldown nach **`citisignal_mobile_subscriptions`**.

![AJO OC](./images/ajooc19.png)

Wählen Sie **`subscription_id`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc20.png)

Aktivieren Sie den Umschalter für **Aggregatdaten**. Wählen Sie dann Folgendes aus:

- **Aggregatfunktion**: **count**
- **Operator**: **größer oder gleich**
- **Wert**: **1**

Klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc21.png)

Sie sollten das dann sehen. Klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc22.png)

### Zielgruppe 2 erstellen

Klicken Sie auf das Symbol **+** auf dem nächsten Knoten im anderen Pfad.

![AJO OC](./images/ajooc23.png)

Wählen Sie **Zielgruppe aufbauen** aus.

![AJO OC](./images/ajooc24.png)

Klicken Sie, um den Ordner für &quot;**&quot;** öffnen.

![AJO OC](./images/ajooc25.png)

Wählen Sie **`--aepUserLdap--_mobile_subscriptions`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc26.png)

Klicken Sie **Zielgruppe erstellen**.

![AJO OC](./images/ajooc27.png)

Klicken Sie **Bedingung hinzufügen**.

![AJO OC](./images/ajooc28.png)

Wählen Sie **subscription_status** aus und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc29.png)

Geben Sie **`active`** in das Feld **Wert** ein. Klicken Sie dann auf **Bedingung hinzufügen**.

![AJO OC](./images/ajooc30.png)

Wählen Sie **`is_upgrade_eligible`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc31.png)

Legen Sie den **Wert** auf **true** fest

![AJO OC](./images/ajooc32.png)

Klicken Sie **Berechnen** um eine Schätzung der Profile anzuzeigen, die für diese Zielgruppe qualifiziert sind. Klicken Sie dann auf **Bestätigen**

![AJO OC](./images/ajooc33.png)

### Aufspaltung

Klicken Sie auf das Symbol **+** und wählen Sie dann **Aufspaltung** aus.

![AJO OC](./images/ajooc34.png)

Ändern Sie das Feld **Bezeichnung** in **90/10 Behandlung vs. Kontrolle**. Klicken Sie, um das Objekt &quot;**&quot;** öffnen.

![AJO OC](./images/ajooc35.png)

Aktivieren Sie den Umschalter für **Grenzwert aktivieren** und legen Sie **Größenbeschränkung** auf **10 Prozent**.

![AJO OC](./images/ajooc36.png)

Klicken Sie **Segment hinzufügen** und Sie sollten sehen, wie **Ergebnis**-Objekt hinzugefügt wird.

Klicken Sie auf **Speichern**.

![AJO OC](./images/ajooc37.png)

### Speichern einer Zielgruppe

Klicken Sie auf das Symbol **+** und wählen Sie **Audience speichern**.

![AJO OC](./images/ajooc38.png)

Legen Sie das Feld **Zielgruppentitel** auf **`--aepUserLdap-- - Control Group`** fest. Klicken Sie **Zielgruppen-Mapping hinzufügen**.

![AJO OC](./images/ajooc39.png)

Drilldown zur **Zielgruppendimension**.

![AJO OC](./images/ajooc40.png)

Wählen Sie **`account_id`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc41.png)

### Anreicherung: Internetabonnement

Klicken Sie auf das Symbol **+**.

![AJO OC](./images/ajooc42.png)

Wählen Sie **Anreicherung** aus.

![AJO OC](./images/ajooc43.png)

Sie sollten das dann sehen. Klicken Sie auf **Anreicherungsdaten hinzufügen**.

![AJO OC](./images/ajooc44.png)

Drilldown nach **`Targeting dimension`**.

![AJO OC](./images/ajooc44a.png)

Drilldown nach **`citisignal_accounts`**.

![AJO OC](./images/ajooc45.png)

Drilldown nach **`citisignal_internet_subscriptions`**.

![AJO OC](./images/ajooc45a.png)

Wählen Sie **`account_id`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc46.png)

Sie sollten das dann sehen. Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc47.png)

Wählen Sie **`subscription_status`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc48.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc49.png)

Wählen Sie **`connection_type`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc50.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc51.png)

Wählen Sie **`service_city`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc52.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc53.png)

Wählen Sie **`avg_dowload_usage_gb`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc54.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc55.png)

Wählen Sie **`data_cap_gb`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc56.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc57.png)

Wählen Sie **`advertised_speed_mbps`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc58.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc59.png)

Wählen Sie **`monthly_recurring_charge`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc60.png)

Klicken Sie auf **Speichern**.

![AJO OC](./images/ajooc61.png)

Scrollen Sie nach oben und ändern Sie das Feld **Beschriftung** in `Enrichment: Internet Subscription`.

![AJO OC](./images/ajooc61a.png)

### Anreicherung: Mobilgeräte-Abonnement

Klicken Sie auf das Symbol **+** auf dem nächsten Knoten und wählen Sie **Anreicherung** aus.

![AJO OC](./images/ajooc62.png)

Ändern Sie das Feld **Beschriftung** in `Enrichment: Mobile Devices Subscription` und klicken Sie dann auf **Anreicherungsdaten hinzufügen**.

![AJO OC](./images/ajooc63.png)

Drilldown zur **Zielgruppendimension**.

![AJO OC](./images/ajooc64.png)

Drilldown nach **`citisignal_mobile_subscriptions`**.

![AJO OC](./images/ajooc65.png)

Wählen Sie **`account_id`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc66.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc67.png)

Wählen Sie **`subscription_id`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc68.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc69.png)

Wählen Sie **`phone_number`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc70.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc71.png)

Wählen Sie **`renewal_eligibility_date`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc72.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc73.png)

Wählen Sie **`line_user_recipient_id`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc74.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc75.png)

Wählen Sie **`is_upgrade_eligible`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc76.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc77.png)

Wählen Sie **`current_device_id`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc78.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc79.png)

Wählen Sie **`contract_start_date`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc80.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc81.png)

Drilldown nach **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc82.png)

Wählen Sie **`model`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc83.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc86.png)

Drilldown nach **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc87.png)

Wählen Sie **`manufacturer`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc88.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc89.png)

Drilldown nach **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc90.png)

Wählen Sie **`device_age_months`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc91.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc92.png)

Drilldown nach **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc93.png)

Wählen Sie **`is_upgrade_eligible`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc94.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc95.png)

Drilldown nach **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc96.png)

Wählen Sie **`recommended_upgrade_product_id`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc97.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc98.png)

Drilldown nach **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc99.png)

Wählen Sie **`monthly_payment`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc100.png)

Klicken Sie **Attribut hinzufügen**.

![AJO OC](./images/ajooc101.png)

Drilldown nach **`citisignal_equipment_subscriptions`**.

![AJO OC](./images/ajooc102.png)

Aktivieren Sie den Umschalter für **Sortierung aktivieren**. Verwenden Sie das Symbol **Bearbeiten**.

![AJO OC](./images/ajooc103.png)

Wählen Sie **`phone_number`** und klicken Sie auf **Bestätigen**.

![AJO OC](./images/ajooc104.png)

Sie sollten dann diese haben.

![AJO OC](./images/ajooc105.png)




Sie sollten dann diese haben. Klicken Sie auf **Speichern**.

![AJO OC](./images/ajooc80a.png)














![AJO OC](./images/ajooc103.png)


## Nächste Schritte

Zurück zu [Adobe Journey Optimizer: Orchestrierte Kampagnen](./ajocampaigns.md){target="_blank"}

Zurück zu [Alle Module](./../../../../overview.md){target="_blank"}
