---
title: "Recevoir des IDOC de SAP dans un contexte transactionnel à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactional context
- IDOCs, receiving in a transactional context using BizTalk Server
ms.assetid: 6a01bb82-7292-4b70-8ad7-996d389a9365
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fd886cfb0e8ba175c22b5d55f12a4866a68921e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server"></a>Recevoir des IDOC de SAP dans un contexte transactionnel à l’aide de BizTalk Server
Recevoir des IDOC dans un contexte transactionnel est similaire à la réception tRFCs dans un contexte transactionnel. Dans ce cas, l’IDOC reçu à partir du système SAP contient un TID fait partie de la  *\<TransactionalRfcOperationIdentifier >* élément. Cette TID est conservée dans une base de données SQL par l’adaptateur. Si le code dans le système SAP qui envoie l’IDOC ABAP a une instruction « COMMIT WORK », le TID est supprimé de la base de données SQL après l’envoi d’une réponse sur le système SAP.  
  
 L’orchestration permet de recevoir un IDOC est similaire, quelles que soient les si l’IDOC est reçu dans un contexte transactionnel ou non. Consultez [recevoir des IDOC de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md). Toutefois, vous devez effectuer certaines tâches supplémentaires pour vous assurer que les IDOC sont reçus dans un contexte transactionnel.  
  
1.  Au moment du design, générer le schéma pour un IDOC que vous souhaitez recevoir.  
  
2.  Au moment de l’exécution, assurez-vous que vous définissez la propriété binding **TidDatabaseConnectionString**. Cette propriété prend la chaîne de connexion pour se connecter à une base de données SQL pour stocker le TID. Un exemple de chaîne de connexion ressemble à :  
  
    ```  
    Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
    ```  
  
     Pour plus d’informations sur la propriété de liaison et comment le configurer, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant Installation installe SQL script, SapAdapter-DbScript-Install.sql, qui doit être exécutée par l’administrateur SQL Server pour créer une base de données et les objets de base de données dans SQL Server. Le script est généralement installé sur  *\<lecteur d’installation >*: programme FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
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
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)