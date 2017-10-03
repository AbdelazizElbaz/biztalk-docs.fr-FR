---
title: "Configurer l’action SOAP pour l’adaptateur Siebel dans BizTalk | Documents Microsoft"
description: "Entrez une action SOAP dans Visual Studio, ou utiliser l’adaptateur WCF-Custom ou WCF-Siebel dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f22a4691-0355-4f08-a14e-e90a3c987ac0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b851aa0b26d80a43f5a839232298ace5507f471b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-siebel"></a>Configuration de l’action SOAP pour Siebel
Pour effectuer des opérations sur le système Siebel à l’aide de la station de travail WCF [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], les utilisateurs de l’adaptateur doivent spécifier une action SOAP. L’action SOAP communique à l’adaptateur quelle action doit être effectuée. Vous pouvez spécifier l’action SOAP au moment du design ou au moment de l’exécution. Toutefois, si vous spécifiez l’action SOAP à la fois au moment du design et moment de l’exécution, l’action que vous avez spécifié au moment du design est remplacée.  
  
 Pour plus d’informations sur la spécification d’action SOAP, consultez [spécifiant les Actions SOAP pour les adaptateurs d’envoi WCF](../../core/specifying-soap-actions-for-wcf-send-adapters.md).
  
## <a name="enter-soap-action-at-design-time"></a>Entrez l’Action SOAP au moment du Design  
 Pour le moment du design, vous devez spécifier l’action SOAP dans le cadre de l’orchestration en incluant une forme expression.  
  
1.  Dans BizTalk orchestration incluent une forme Expression en le faisant glisser à partir de la **Orchestration BizTalk** boîte à outils.  
  
2.  Double-cliquez sur le **Expression** forme pour ouvrir l’éditeur d’Expression BizTalk.  
  
3.  Spécifiez l’action dans l’éditeur d’Expression BizTalk. Exemple :  
  
    ```  
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"  
    ```  
  
     Pour plus d’informations sur **Expression** forme et l’éditeur d’Expression BizTalk, consultez [comment créer des Expressions](../../core/how-to-create-expressions.md).  
  
## <a name="enter-soap-action-at-run-time"></a>Entrez l’Action SOAP en cours d’exécution  
 Temps d’exécution, vous devez spécifier l’action SOAP dans le cadre de la boîte de dialogue de propriétés du port WCF-Custom ou WCF-Siebel.  
  
#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a>Entrez une action SOAP pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.  
  
5.  Dans le **Action** texte, spécifiez l’action SOAP pour l’opération. Vous pouvez spécifier l’action comme suit :  
  
    -   **En utilisant le format d’action unique**. Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération. Exemple :  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    -   **En utilisant le format de mappage d’action**. Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations. Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour effectuer une opération d’insertion sur le composant de compte d’entreprise) et Op2 (pour effectuer une opération de mise à jour sur le composant de compte d’entreprise), l’action SOAP peut être spécifiée dans les éléments suivants manière :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update " />  
        </BtsActionMapping>  
        ```  
  
         Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.  
  
         Le format de l’action SOAP est différent pour chaque opération. Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).
  
#### <a name="enter-a-soap-action-for-the-wcf-siebel-port"></a>Entrez une action SOAP pour le port WCF-Siebel  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** liste déroulante, sélectionnez le WCF-Siebel adaptateur vous ajoutez précédemment, puis cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du port, cliquez sur le **général** onglet.  
  
6.  Dans le **Action** texte, spécifiez l’action SOAP pour l’opération. Vous pouvez spécifier l’action comme suit :  
  
    -   **En utilisant le format d’action unique**. Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération. Exemple :  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    -   **En utilisant le format de mappage d’action**. Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations. Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour effectuer une opération d’insertion sur le composant de compte d’entreprise) et Op2 (pour effectuer une opération de mise à jour sur le composant de compte d’entreprise), l’action SOAP peut être spécifiée dans les éléments suivants manière :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update " />  
        </BtsActionMapping>  
        ```  
  
         Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.  
  
         Le format de l’action SOAP est différent pour chaque opération. Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)