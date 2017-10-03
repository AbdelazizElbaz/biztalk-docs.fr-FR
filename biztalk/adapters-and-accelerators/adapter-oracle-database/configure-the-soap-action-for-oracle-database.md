---
title: "Configurer l’action SOAP pour la base de données Oracle dans BizTalk | Documents Microsoft"
description: "Entrez une action SOAP dans Visual Studio, ou utiliser l’adaptateur WCF-Custom ou WCF-OracleDB dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d21cca-3907-4f99-af76-c1e7286e1bcf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2577a221385cdef2e210798b3e8170433ff0e48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-soap-action-for-oracle-database"></a>Configurer l’action SOAP pour la base de données Oracle
Pour effectuer toutes les opérations sur la base de données Oracle à l’aide de la station de travail WCF [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], les utilisateurs de l’adaptateur doivent entrer une action SOAP. L’action SOAP communique à l’adaptateur quelle action doit être terminée. Vous pouvez entrer l’action SOAP au moment du design ou au moment de l’exécution. Toutefois, si vous entrez l’action SOAP à la fois au moment du design et moment de l’exécution, l’action que vous entrez au moment du design est modifiée.  
  
 Pour plus d’informations sur la spécification d’action SOAP, consultez [spécifiant les Actions SOAP pour les adaptateurs d’envoi WCF](../../core/specifying-soap-actions-for-wcf-send-adapters.md).  
  
## <a name="enter-soap-action-from-visual-studio"></a>Entrez l’Action SOAP à partir de Visual Studio  
 À partir de Visual Studio, vous devez spécifier l’action SOAP dans le cadre de l’orchestration en utilisant une **Expression** forme.  
  
1.  Dans l’orchestration BizTalk, vous devez inclure une **Expression** forme en le faisant glisser à partir de la **Orchestration BizTalk** boîte à outils.  
  
2.  Double-cliquez sur le **Expression** forme pour ouvrir l’éditeur d’Expression BizTalk.  
  
3.  Spécifiez l’action dans l’éditeur d’Expression BizTalk. Exemple :  
  
    ```
    OutboundMessage(WCF.Action)="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"  
    ```  
  
     Pour plus d’informations sur **Expression** forme et l’éditeur d’Expression BizTalk, consultez [comment créer des Expressions](../../core/how-to-create-expressions.md).  
  
## <a name="enter-soap-action-from-biztalk-server-administration"></a>Entrez l’Action SOAP à partir de l’Administration de BizTalk Server  
 Dans la console Administration de BizTalk Server, vous devez spécifier l’action SOAP dans le cadre de la configuration du port WCF-Custom ou WCF-OracleDB. 

#### <a name="enter-a-soap-action-for-the-wcf-custom-port"></a>Entrez une action SOAP pour le port WCF-Custom  
 
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.  
  
5.  Dans le **Action** texte, spécifiez l’action SOAP pour l’opération. Vous pouvez spécifier l’action comme suit :  
  
    -   **En utilisant le format d’action unique**. Utilisez ce format si WCF-Custom port envoie et recevoir des messages pour une seule opération. Exemple :  
  
        ```  
        http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
        ```  
  
    -   **En utilisant le format de mappage d’action**. Utilisez ce format, si un seul port WCF-Custom envoie et reçoit des messages pour plusieurs opérations. Par exemple, si un seul port WCF-Custom envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table EMP) et Op2 (pour mettre à jour des enregistrements dans la table EMP), l’action SOAP peut être spécifiée de la manière suivante :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
        </BtsActionMapping>  
        ```  
  
         Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.  
  
         Le format de l’action SOAP est différent pour chaque opération. Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de Message](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).  
  
#### <a name="enter-a-soap-action-for-the-wcf-oracledb-port"></a>Entrez une action SOAP pour le port WCF-OracleDB  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-OracleDB à la console Administration de BizTalk Server. Pour obtenir des instructions, consultez [Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez le port WCF-OracleDB que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **général** onglet.  
  
6.  Dans le **Action** texte, spécifiez l’action SOAP pour l’opération. Vous pouvez spécifier l’action comme suit :  
  
    -   **En utilisant le format d’action unique**. Utilisez ce format si le WCF-OracleDB port envoie et recevoir des messages pour une seule opération. Exemple :  
  
        ```  
        http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert  
        ```  
  
    -   **En utilisant le format de mappage d’action**. Utilisez ce format, si un seul port WCF-OracleDB envoie et reçoit des messages pour plusieurs opérations. Par exemple, si un seul port WCF-OracleDB envoie et reçoit des messages pour Op1 (pour insérer des enregistrements dans la table EMP) et Op2 (pour mettre à jour des enregistrements dans la table EMP), l’action SOAP peut être spécifiée de la manière suivante :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Op1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert" />  
          <Operation Name="Op2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update " />  
        </BtsActionMapping>  
        ```  
  
         Cette approche offre une plus grande flexibilité en termes de spécification d’un ensemble d’actions et par conséquent, l’activation de messages appartenant à des types d’actions différentes de circuler via le même port.  
  
         Le format de l’action SOAP est différent pour chaque opération. Pour plus d’informations sur le format d’action pour chaque opération, consultez [Messages et des schémas de Message](messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)