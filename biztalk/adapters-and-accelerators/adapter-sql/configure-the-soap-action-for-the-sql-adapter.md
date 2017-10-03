---
title: "Configurer l’action SOAP pour l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "Entrez une action SOAP dans Visual Studio, ou utiliser l’adaptateur WCF-Custom ou WCF-SQL dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acd7f60b-c27f-4988-a67c-e56ef8d38f66
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4e342353b13848cca1c332d4568f541e59924cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-the-sql-adapter"></a>Configurer l’action SOAP pour l’adaptateur SQL
Pour effectuer une quelconque opération sur SQL Server à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez spécifier une action SOAP. L’action SOAP communique à l’adaptateur quelle action doit être effectuée. Vous pouvez spécifier l’action SOAP à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Toutefois, si vous spécifiez l’action SOAP à partir de deux emplacements, l’action vous avez spécifié à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sera remplacé.  
  
 Pour plus d’informations sur la spécification d’action SOAP, consultez [spécifiant les Actions SOAP pour les adaptateurs d’envoi WCF](../../core/specifying-soap-actions-for-wcf-send-adapters.md).
  
## <a name="enter-the-soap-action-in-visual-studio"></a>Entrez l’action SOAP dans Visual Studio  
 À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier l’action SOAP dans le cadre de l’orchestration en utilisant une **Expression** forme.  
  
1.  Dans l’orchestration BizTalk, vous devez inclure une **Expression** forme en le faisant glisser à partir de la **Orchestration BizTalk** boîte à outils.  
  
2.  Double-cliquez sur le **Expression** forme pour ouvrir l’éditeur d’Expression BizTalk.  
  
3.  Spécifiez l’action dans Éditeur d’Expression BizTalk. Exemple :  
  
    ```  
    OutboundMessage(WCF.Action)="TableOp/Insert/dbo/Employee"  
    ```  
  
     Pour plus d’informations sur la **Expression** forme et l’éditeur d’Expression BizTalk, consultez [comment créer des Expressions](../../core/how-to-create-expressions.md).
  
## <a name="enter-the-soap-action-from-the-biztalk-server-administration-console"></a>Entrez l’action SOAP à partir de la console Administration de BizTalk Server  
 À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous pouvez spécifier l’action SOAP dans le cadre de la configuration du port WCF-Custom ou WCF-SQL.  
  
### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a>Entrez une action SOAP pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.  
  
5.  Dans le **Action** texte, spécifiez l’action SOAP pour l’opération. Vous pouvez spécifier l’action comme suit :  
  
    -   **En utilisant le format d’action unique**. Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération. Exemple :  
  
        ```  
        TableOp/Insert/dbo/Employee  
        ```  
  
    -   **En utilisant le format de mappage d’action**. Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations. Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table Employee) et Op2 (pour mettre à jour des enregistrements dans la table Employee), l’action SOAP peut être spécifiée de la manière suivante :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
          <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
        </BtsActionMapping>  
        ```  
  
         L’approche de mappage d’action fournit une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages qui appartiennent à une action différente des types de circuler via le même port.  
  
         Le format de l’action SOAP est différent pour chaque opération. Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).
  
### <a name="enter-a-soap-action-for-the-wcf-sql-port"></a>Entrez une action SOAP pour le port WCF-SQL  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-SQL pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SQL que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **général** onglet.  
  
6.  Dans le **Action** texte, spécifiez l’action SOAP pour l’opération. Vous pouvez spécifier l’action comme suit :  
  
    -   **En utilisant le format d’action unique**. Utilisez ce format si le WCF-SQL port envoie et recevoir des messages pour une seule opération. Exemple :  
  
        ```  
        TableOp/Insert/dbo/Employee  
        ```  
  
    -   **En utilisant le format de mappage d’action**. Utilisez ce format, si un seul port WCF-SQL envoie et reçoit des messages pour plusieurs opérations. Par exemple, si un seul port WCF-SQL envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table Employee) et Op2 (pour mettre à jour des enregistrements dans la table Employee), l’action SOAP peut être spécifiée de la manière suivante :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="TableOp/Insert/dbo/Employee" />  
          <Operation Name="Op2" Action="TableOp/Update/dbo/Employee" />  
        </BtsActionMapping>  
        ```  
  
         L’approche de mappage d’action fournit une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages qui appartiennent à une action différente des types de circuler via le même port.  
  
         Le format de l’action SOAP est différent pour chaque opération. Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de message](messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)