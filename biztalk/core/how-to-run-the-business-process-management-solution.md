---
title: "Comment exécuter la Solution de gestion des processus métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, validating
- process management solution tutorial, submitting orders
- process management solution tutorial, stopping orders
- process management solution tutorial, updating orders
ms.assetid: cb77651e-e16c-49dc-9f8a-88584cd68a8b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3997fb18e7498ab2bc5f8c77b53740fb87ab6f93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-run-the-business-process-management-solution"></a>Exécution de la solution de gestion des processus d'entreprise
Les procédures suivantes décrivent l'exécution et la validation d'une solution de gestion des processus d'entreprise sur un seul ordinateur.  
  
-   [Démarrer la Solution gestion des processus d’entreprise](#step1)  
  
-   [Exécution et la validation de la Solution gestion des processus d’entreprise](#step3)  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’exécuter la solution de gestion des processus métiers, vous devez effectuer les étapes de [l’installation de la Solution de gestion des processus métier](../core/how-to-install-the-business-process-management-solution.md).  
  
##  <a name="step1"></a>Démarrer la Solution gestion des processus d’entreprise  
  
#### <a name="to-start-the-business-process-management-solution"></a>Pour démarrer la solution de gestion des processus d'entreprise  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, développez **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **Démarrer**.  
  
3.  Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, puis développez **Applications**.  
  
    1.  Sur BTSScn.BPM.MessagingApp, cliquez **Démarrer**, puis cliquez sur **Démarrer** sur la **démarrer l’Application** boîte de dialogue.  
  
    2.  Sur BTSScn.BPM.OrderBrokerApp, cliquez **Démarrer**, puis cliquez sur **Démarrer** sur la **démarrer l’Application** boîte de dialogue.  
  
    3.  Sur BTSScn.BPM.CableOrderApp, cliquez **Démarrer**, puis cliquez sur **Démarrer** sur la **démarrer l’Application** boîte de dialogue.  
  
    4.  Cliquez sur BTSScn.BPM.OrderBrokerApp.Test, puis cliquez sur **arrêter**. Dans le **arrêter l’Application** boîte de dialogue, sélectionnez **arrêt complet - arrêter l’instance**, puis cliquez sur **arrêter**.  
  
    > [!NOTE]
    >  Pour insérer des informations dans la base de données de l’historique. l’orchestration OrderBroker utilise le port d’envoi historyport dont le **accusé de réception** propriété a la valeur **transmis**. Le port d'envoi est lié au groupe d'envoi HistoryInsert-SPG qui inclut les ports d'envoi HistoryInsert-SP et HistoryInsert-Test-SP. Pour ces deux ports d'envoi, le moteur de messagerie publie deux accusés de réception sur l'orchestration OrderBroker. Il interrompt l'orchestration en raison de messages non utilisés. Pour éviter cette situation, vous devez désinscrire l'un des ports d'envoi. Dans cette procédure pas à pas, désinscrivez le port d'envoi HistoryInsert-Test-SP en arrêtant complètement l'application BTSScn.BPM.OrderBrokerApp.Test. Pour plus d’informations sur l’orchestration OrderBroker, consultez [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md). Pour plus d’informations sur **accusé de réception** propriété, consultez [accusés de réception à l’aide de](../core/using-acknowledgments.md).  
  
4.  Exécutez le simulateur d'installations comme suit :  
  
    1.  Ouvrez une invite de commandes, accédez au dossier %BTSSolutionsPath%\BPM\FacilitiesSimulator\bin\debug.  
  
    2.  Type `BTSScnBPMFacilities.exe`, puis appuyez sur ENTRÉE. Maintenez l'exécution du simulateur d'installations. Cette application simule les systèmes principaux de traitement des installations à Southridge Video.  
  
    3.  Dans le simulateur d'installations, tapez les files d'attente de réception et de transmission suivantes :  
  
        |Nom|Valeur|  
        |----------|-----------|  
        |**File d’attente de réception**|`.\private$\ToFacilitiesQ`|  
        |**File d’attente de transmission**|`.\private$\FromFacilitiesQ`|  
  
    4.  Dans le simulateur d’installations, cliquez sur **Démarrer**.  
  
5.  Exécutez le serveur d'opérations comme suit :  
  
    1.  Ouvrez une nouvelle invite de commandes, accédez au dossier %BTSSolutionsPath%\BPM\OperationsServer\bin\debug.  
  
    2.  Type `BTSScnBPMOperations.exe 8881` à l’invite de commandes et appuyez sur ENTRÉE. Maintenez l'exécution du serveur d'opérations. Le serveur d'opérations écoute sur le port TCP, 8881, pour recevoir des messages d'erreur de l'adaptateur Ops. Il affiche les messages d'erreur reçus par l'adaptateur Ops.  
  
6.  Exécutez le système d'approvisionnement en câble comme suit :  
  
    1.  Ouvrez une nouvelle invite de commandes, accédez au dossier %BTSSolutionsPath%\BPM\CableProvisioningSystemServer\bin\debug.  
  
    2.  Type `BTSScnBPMProvisioning.exe 8880`, puis appuyez sur ENTRÉE. Puis, maintenez l'exécution du système d'approvisionnement en câble. Le système d'approvisionnement en câble écoute sur le port TCP, 8880. Cette application simule un système de commande principal, puis affiche les commandes finales.  
  
##  <a name="step3"></a>Exécution et la validation de la Solution gestion des processus d’entreprise  
  
#### <a name="to-submit-a-new-order-and-validate-the-solution"></a>Pour envoyer une nouvelle commande et valider la solution  
  
1.  Dans Internet Explorer, dans le **adresse** zone, tapez l’URL de l’application Web Service clientèle comme suit :  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une nouvelle commande dans le tableau suivant, puis cliquez sur **envoyer la commande.**  
  
    |Entrée|Valeur|  
    |-----------|-----------|  
    |ID de client|1|  
    |Order ID|1|  
    |Numéro de séquence|1|  
    |Code du type de service|Nouveau service standard|  
  
3.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :  
  
     **ID de commande client ID 1 1 numéro de séquence 1**  
  
4.  Examinez la commande placée à l'invite de commandes exécutant le système d'approvisionnement en câble. L'application affiche les messages indiquant que la commande envoyée est analysée, activée, puis terminée.  
  
5.  Assurez-vous que le nombre total de messages est incrémenté d'un sur le simulateur d'installations.  
  
#### <a name="to-submit-a-duplicate-while-the-biztalk-server-is-processing-the-original-order"></a>Pour envoyer une copie lorsque BizTalk Server traite la commande d'origine  
  
1.  Dans Internet Explorer, dans le **adresse** zone, tapez l’URL de l’application Web Service clientèle comme suit :  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  Dans le simulateur d’installations, cliquez sur **arrêter**. Cela empêche les commandes envoyées de poursuivre leur traitement.  
  
3.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une nouvelle commande dans le tableau suivant, puis cliquez sur **envoyer la commande** à deux reprises pour simuler des commandes en double.  
  
    |Entrée|Valeur|  
    |-----------|-----------|  
    |ID de client|2|  
    |Order ID|1|  
    |Numéro de séquence|1|  
    |Code du type de service|Nouveau service standard|  
  
4.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :  
  
     **ID de commande client ID 2 1 numéro de séquence 1**  
  
5.  Dans le simulateur d’installations, cliquez sur **Démarrer**. Les orchestrations en attente de réponses du simulateur d'installations reprennent. Cela simule l'envoi d'une commande en double pendant le traitement de la première commande.  
  
6.  Examinez les commandes placées à l'invite de commandes exécutant le système d'approvisionnement en câble. L'application affiche les messages indiquant que seule la première commande est analysée, activée, puis terminée.  
  
7.  Examinez le message d'erreur pour rechercher les commandes en double à l'invite de commandes exécutant le serveur d'opérations.  
  
#### <a name="to-update-an-order-while-the-biztalk-server-is-processing-the-order"></a>Pour mettre à jour une commande lorsque BizTalk Server traite la commande  
  
1.  Dans Internet Explorer, dans le **adresse** zone, tapez l’URL de l’application Web Service clientèle comme suit :  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  Dans le simulateur d’installations, cliquez sur **arrêter**.  
  
3.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une nouvelle commande dans le tableau suivant, puis cliquez sur **envoyer la commande**.  
  
    |Entrée|Valeur|  
    |-----------|-----------|  
    |ID de client|3|  
    |Order ID|1|  
    |Numéro de séquence|1|  
    |Code du type de service|Nouveau service standard|  
  
4.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :  
  
     **ID de commande client ID 3 1 numéro de séquence 1**  
  
5.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une commande de mise à jour dans le tableau suivant, puis cliquez sur **envoyer la commande**.  
  
    |Entrée|Valeur|  
    |-----------|-----------|  
    |ID de client|3|  
    |Order ID|1|  
    |Numéro de séquence|2|  
    |Code du type de service|Nouveau service Deluxe|  
  
6.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :  
  
     **ID de commande client ID 3 1 numéro de séquence 2**  
  
7.  Dans le simulateur d’installations, cliquez sur **Démarrer**  
  
8.  Vérifiez le message de résultat sur la **formulaire entrée de commande Southridge Video client Service Rep** page.  
  
9. Examinez les commandes placées à l'invite de commandes exécutant le système d'approvisionnement en câble. L'application affiche les messages indiquant que deux commandes sont analysées mais que seule la commande mise à jour est activée et terminée.  
  
10. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **Observateur d’événements**et vérifiez ensuite un nouveau avertissement qui le ordre d’origine a été interrompue.  
  
11. Examinez le message d'erreur d'échec de routage à l'invite de commandes exécutant le serveur d'opérations.  
  
    > [!NOTE]
    >  Il y a une erreur dans le journal des événements et sur le serveur d'opérations. Le message de réponse du système d'installations n'est plus corrélé à une instance du processus d'entreprise car il a été terminé par l'interruption causée par la nouvelle commande avec un numéro de séquence supérieur. Par conséquent, le message de réponse est orphelin et routé vers le serveur d'opérations. Pour plus d’informations sur les mises à jour, consultez [via le Gestionnaire de processus de flux de commande](../core/order-flow-through-the-process-manager.md).  
  
12. Ouvrez le dernier message dans le dossier %SystemDrive%:\BPMTest\HistoryUpdate-SP dans le Bloc-notes. Vérifiez **CustName**, **OrderNum**, **OrderSeqNum**, et **état** champs pour voir si le message a été créé pour la nouvelle commande et le **État** champ est **terminé**.  
  
#### <a name="to-terminate-an-order-while-the-biztalk-server-is-processing-the-order"></a>Pour terminer une commande lorsque BizTalk Server traite la commande  
  
1.  Dans Internet Explorer, dans le **adresse** zone, tapez l’URL de l’application Web Service clientèle comme suit :  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  Dans le simulateur d’installations, cliquez sur **arrêter**.  
  
3.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une nouvelle commande dans le tableau suivant, puis cliquez sur **envoyer la commande**.  
  
    |Entrée|Valeur|  
    |-----------|-----------|  
    |ID de client|4|  
    |Order ID|1|  
    |Numéro de séquence|1|  
    |Code du type de service|Nouveau service standard|  
  
4.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :  
  
     **ID de commande client ID 4 1 numéro de séquence 1**  
  
5.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** , cliquez sur **terminer la commande**.  
  
6.  Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :  
  
     **ID de commande client ID 4 1 numéro de séquence 1**  
  
7.  Dans le simulateur d’installations, cliquez sur **Démarrer**.  
  
8.  Examinez les commandes placées à l'invite de commandes exécutant le système d'approvisionnement en câble. L'application affiche les messages indiquant que la commande est uniquement analysée et activée.  
  
9. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **Observateur d’événements**et vérifiez ensuite un nouveau avertissement qui le commande a été arrêté par l’utilisateur.  
  
    > [!NOTE]
    >  Pour plus d’informations sur l’arrêt des commandes, consultez [via le Gestionnaire de processus de flux de commande](../core/order-flow-through-the-process-manager.md).  
  
10. Examinez le message d'erreur d'échec de routage à l'invite de commandes exécutant le serveur d'opérations.  
  
## <a name="see-also"></a>Voir aussi  
 [Avant d’installer la Solution gestion des processus d’entreprise](../core/before-installing-the-business-process-management-solution.md)   
 [Programme d’installation de développeur Machine pour la Solution gestion des processus d’entreprise](../core/developer-machine-setup-for-the-business-process-management-solution.md)