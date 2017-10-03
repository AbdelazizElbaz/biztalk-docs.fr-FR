---
title: "À partir de SAP à l’aide de BizTalk Server de réception entrant tRFC appels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFC calls, receiving using BizTalk Server
- tRFCs, sample
ms.assetid: 500eedea-3d27-478c-a64c-903a1fa2b02f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3ad06768a5156b71d4d0da77b778f22d3d09fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-inbound-trfc-calls-from-sap-using-biztalk-server"></a>Réception entrant tRFC appelle à partir de SAP à l’aide de BizTalk Server
Un appel de serveur tRFC est un appel de serveur RFC transactionnels. L’orchestration permet de recevoir une commande RFC dans un contexte transactionnel est similaire à l’orchestration de recevoir toutes les autres RFC entrant envoyé à partir d’un système SAP. Toutefois, vous devez effectuer certaines tâches supplémentaires pour vous assurer que les documents RFC sont reçus dans un contexte transactionnel. Pour plus d’informations sur la réception d’une demande de changement de trafic entrant du système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [recevoir les appels RFC entrants à partir de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md). Pour plus d’informations sur la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge de recevoir des appels de tRFC entrant à partir d’un système SAP, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
 Réception d’un tRFC entrant envoyé à partir d’un système SAP est similaire à la réception d’une commande RFC entrante, avec les différences suivantes :  
  
1.  Au moment du design, lors de la génération du schéma, veillez à sélectionner le tRFC sous le **TRFC** nœud.  
  
2.  Au moment de l’exécution, assurez-vous que vous définissez la propriété binding **TidDatabaseConnectionString**. Cette propriété prend la chaîne de connexion pour se connecter à une base de données SQL pour stocker le TID. Un exemple de chaîne de connexion ressemble à :  
  
    ```  
    Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
    ```  
  
     Pour plus d’informations sur la propriété de liaison et comment le configurer, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant Installation installe SQL script, SapAdapter-DbScript-Install.sql, qui doit être exécutée par l’administrateur SQL Server pour créer une base de données et les objets de base de données dans SQL Server. Le script est généralement installé sur  *\<lecteur d’installation > : programme FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]* .  
    >   
    >  Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise ces objets pour conserver le TID. Par conséquent, l’administrateur SQL Server devez vous assurer que le nom d’utilisateur assure que la partie de la chaîne de connexion dispose des privilèges suffisants pour exécuter les procédures stockées. Vous pouvez également choisir pour l’authentification Windows à condition que l’utilisateur Windows dispose des autorisations suffisantes pour exécuter des procédures stockées dans la base de données.  
  
3.  Vérifiez que MSDTC est activé sur l’ordinateur sur lequel l’adaptateur est installé. Procédez comme suit pour activer le service MSDTC.  
  
    1.  Démarrez le composant logiciel enfichable MMC Services de composants.  
  
    2.  Dans le composant logiciel enfichable MMC Services de composants, dans le volet gauche, développez **Services de composants**, développez **ordinateurs**, avec le bouton droit **poste**, puis cliquez sur  **Propriétés**.  
  
    3.  Dans le **propriétés Poste de travail** boîte de dialogue, cliquez sur le **MSDTC** onglet.  
  
    4.  Dans le **Configuration de Transaction** , cliquez sur le **Configuration de la sécurité** bouton.  
  
    5.  Dans le **Configuration de la sécurité** boîte de dialogue, sélectionnez le **accès DTC réseau** et dans ce cas, cochez la **autoriser les Clients distants** case à cocher.  
  
    6.  Dans le **Communication du Gestionnaire de transactions** section, sélectionnez le **autoriser les transactions entrantes** et **autoriser les transactions sortantes** cases à cocher.  
  
    7.  Dans le **Configuration de la sécurité** boîte de dialogue, cliquez sur **OK**.  
  
    8.  Cliquez sur **Oui** dans la boîte dialogue informant que le service MSDTC doit être redémarré. Une fois le service MSDTC est redémarré, cliquez sur **OK** sur la boîte de dialogue.  
  
    9. Dans le **propriétés Poste de travail** boîte de dialogue, cliquez sur **OK**.  
  
4.  Ajouter de MSDTC à la liste d’exceptions de pare-feu Windows, si ce n’est pas déjà ajouté. Exécutez la commande suivante :  
  
    ```  
    netsh firewall set allowedprogram %windir%\system32\msdtc.exe MSDTC enable  
    ```  
  
> [!IMPORTANT]
>  Un appel entrant tRFC est utilisé lors de la réception des IDOC à partir du système SAP dans un contexte « transactionnel ».  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)