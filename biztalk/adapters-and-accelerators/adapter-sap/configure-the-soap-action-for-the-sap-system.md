---
title: "Configurer l’action SOAP pour le système SAP dans BizTalk | Documents Microsoft"
description: "Entrez une action SOAP dans la forme Expression, ou utiliser l’adaptateur WCF-Custom ou WCF-SAP dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76084bc5-7a10-4c4c-be22-bee83779a011
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36a474d53d3fcaf61668800094a1d98d0e061aa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-the-sap-system"></a>Configuration de l’action SOAP pour le système SAP
Pour effectuer des opérations sur le système SAP à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], les utilisateurs de l’adaptateur doivent spécifier une action SOAP. L’action SOAP communique à l’adaptateur quelle action doit être effectuée. Vous pouvez spécifier l’action SOAP au moment du design ou au moment de l’exécution. Toutefois, si vous spécifiez l’action SOAP à la fois au moment du design et moment de l’exécution, l’action que vous avez spécifié au moment du design est remplacée.  
  
 Pour plus d’informations sur la spécification d’action SOAP, consultez [spécifiant les Actions SOAP pour les adaptateurs d’envoi WCF](../../core/specifying-soap-actions-for-wcf-send-adapters.md).
  
## <a name="enter-soap-action-at-design-time"></a>Entrez l’Action SOAP au moment du Design  
 Pour le moment du design, vous devez spécifier l’action SOAP dans le cadre de l’orchestration en incluant une forme expression.  
  
 
1.  Dans l’orchestration BizTalk, inclure une forme Expression en le faisant glisser à partir de la **Orchestration BizTalk** boîte à outils.  
  
2.  Double-cliquez sur le **Expression** forme pour ouvrir l’éditeur d’Expression BizTalk.  
  
3.  Spécifiez l’action dans l’éditeur d’Expression BizTalk. Exemple :  
  
    ```  
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET"  
    ```  
  
     Pour plus d’informations sur la **Expression** forme et l’éditeur d’Expression BizTalk, consultez [comment créer des Expressions](../../core/how-to-create-expressions.md).
  
## <a name="enter-soap-action-at-run-time"></a>Entrez l’Action SOAP en cours d’exécution  
 Temps d’exécution, vous pouvez spécifier l’action SOAP dans le cadre de la configuration du port WCF-Custom ou WCF-SAP.  
  
### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a>Entrez une action SOAP pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.  
  
5.  Dans le **Action** texte, spécifiez l’action SOAP pour l’opération. Vous pouvez spécifier l’action comme suit :  
  
    -   **En utilisant le format d’action unique**. Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération. Exemple :  
  
        ```  
        http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
        ```  
  
    -   **En utilisant le format de mappage d’action**. Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations. Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour appeler RFC_CUSTOMER_GET RFC) et Op2 (pour appeler BAPI_SALESORDER_CREATEFROMDAT2 BAPI), l’action SOAP peut être spécifiée de la manière suivante :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
        </BtsActionMapping>  
        ```  
  
         Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.  
  
         Le format de l’action SOAP est différent pour chaque opération. Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).
  
### <a name="enter-a-soap-action-for-the-wcf-sap-port"></a>Entrez une action SOAP pour le port WCF SAP  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SAP que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **général** onglet.  
  
6.  Dans le **Action** texte, spécifiez l’action SOAP pour l’opération. Vous pouvez spécifier l’action comme suit :  
  
    -   **En utilisant le format d’action unique**. Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération. Exemple :  
  
        ```  
        http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
        ```  
  
    -   **En utilisant le format de mappage d’action**. Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations. Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour appeler RFC_CUSTOMER_GET RFC) et Op2 (pour appeler BAPI_SALESORDER_CREATEFROMDAT2 BAPI), l’action SOAP peut être spécifiée de la manière suivante :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET " />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2" />  
        </BtsActionMapping>  
        ```  
  
         Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.  
  
         Le format de l’action SOAP est différent pour chaque opération. Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)