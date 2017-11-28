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
# <a name="receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server"></a><span data-ttu-id="80c02-102">Recevoir des IDOC de SAP dans un contexte transactionnel à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="80c02-102">Receive IDOCs from SAP in a Transactional Context using BizTalk Server</span></span>
<span data-ttu-id="80c02-103">Recevoir des IDOC dans un contexte transactionnel est similaire à la réception tRFCs dans un contexte transactionnel.</span><span class="sxs-lookup"><span data-stu-id="80c02-103">Receiving IDOC in a transactional context is similar to receiving tRFCs in a transactional context.</span></span> <span data-ttu-id="80c02-104">Dans ce cas, l’IDOC reçu à partir du système SAP contient un TID fait partie de la  *\<TransactionalRfcOperationIdentifier >* élément.</span><span class="sxs-lookup"><span data-stu-id="80c02-104">In such a case, the IDOC received from the SAP system contains a TID as part of the *\<TransactionalRfcOperationIdentifier>* element.</span></span> <span data-ttu-id="80c02-105">Cette TID est conservée dans une base de données SQL par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="80c02-105">This TID is persisted in a SQL database by the adapter.</span></span> <span data-ttu-id="80c02-106">Si le code dans le système SAP qui envoie l’IDOC ABAP a une instruction « COMMIT WORK », le TID est supprimé de la base de données SQL après l’envoi d’une réponse sur le système SAP.</span><span class="sxs-lookup"><span data-stu-id="80c02-106">If the ABAP code in the SAP system that sends the IDOC has a "COMMIT WORK" statement, the TID is deleted from the SQL database after a response is sent back to the SAP system.</span></span>  
  
 <span data-ttu-id="80c02-107">L’orchestration permet de recevoir un IDOC est similaire, quelles que soient les si l’IDOC est reçu dans un contexte transactionnel ou non.</span><span class="sxs-lookup"><span data-stu-id="80c02-107">The orchestration required to receive an IDOC is similar irrespective of whether the IDOC is received in a transactional context or not.</span></span> <span data-ttu-id="80c02-108">Consultez [recevoir des IDOC de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="80c02-108">See [Receive IDOCs from SAP by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md).</span></span> <span data-ttu-id="80c02-109">Toutefois, vous devez effectuer certaines tâches supplémentaires pour vous assurer que les IDOC sont reçus dans un contexte transactionnel.</span><span class="sxs-lookup"><span data-stu-id="80c02-109">However, you need to perform certain additional tasks to make sure the IDOCs are received in a transactional context.</span></span>  
  
1.  <span data-ttu-id="80c02-110">Au moment du design, générer le schéma pour un IDOC que vous souhaitez recevoir.</span><span class="sxs-lookup"><span data-stu-id="80c02-110">At design time, generate the schema for an IDOC that you want to receive.</span></span>  
  
2.  <span data-ttu-id="80c02-111">Au moment de l’exécution, assurez-vous que vous définissez la propriété binding **TidDatabaseConnectionString**.</span><span class="sxs-lookup"><span data-stu-id="80c02-111">At run time, make sure you set the binding property **TidDatabaseConnectionString**.</span></span> <span data-ttu-id="80c02-112">Cette propriété prend la chaîne de connexion pour se connecter à une base de données SQL pour stocker le TID.</span><span class="sxs-lookup"><span data-stu-id="80c02-112">This property takes the connection string to connect to a SQL database to store the TID.</span></span> <span data-ttu-id="80c02-113">Un exemple de chaîne de connexion ressemble à :</span><span class="sxs-lookup"><span data-stu-id="80c02-113">A sample connection string would look like:</span></span>  
  
    ```  
    Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
    ```  
  
     <span data-ttu-id="80c02-114">Pour plus d’informations sur la propriété de liaison et comment le configurer, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="80c02-114">For more information about the binding property and how to set it, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="80c02-115">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant Installation installe SQL script, SapAdapter-DbScript-Install.sql, qui doit être exécutée par l’administrateur SQL Server pour créer une base de données et les objets de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="80c02-115">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard installs a SQL script, SapAdapter-DbScript-Install.sql, which must be run by the SQL Server administrator to create a database and the database objects in SQL Server.</span></span> <span data-ttu-id="80c02-116">Le script est généralement installé sur  *\<lecteur d’installation >*: programme FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80c02-116">The script is typically installed at *\<installation drive>*:Program FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span>  
    >   
    >  <span data-ttu-id="80c02-117">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise ces objets pour conserver le TID.</span><span class="sxs-lookup"><span data-stu-id="80c02-117">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses these objects to persist the TIDs.</span></span> <span data-ttu-id="80c02-118">Par conséquent, l’administrateur SQL Server devez vous assurer que le nom d’utilisateur assure que la partie de la chaîne de connexion dispose des privilèges suffisants pour exécuter les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="80c02-118">So, the SQL Server administrator must ensure that the user name provide as part of the connection string has sufficient privileges to execute the stored procedures.</span></span> <span data-ttu-id="80c02-119">Vous pouvez également choisir pour l’authentification Windows à condition que l’utilisateur Windows dispose des autorisations suffisantes pour exécuter des procédures stockées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="80c02-119">You can also opt for Windows authentication provided the Windows user has sufficient permissions to execute stored procedures in the database.</span></span>  
  
3.  <span data-ttu-id="80c02-120">Vérifiez que MSDTC est activé sur l’ordinateur sur lequel l’adaptateur est installé.</span><span class="sxs-lookup"><span data-stu-id="80c02-120">Make sure MSDTC is enabled on the computer where the adapter is installed.</span></span> <span data-ttu-id="80c02-121">Procédez comme suit pour activer le service MSDTC.</span><span class="sxs-lookup"><span data-stu-id="80c02-121">Perform the following steps to enable MSDTC.</span></span>  
  
    1.  <span data-ttu-id="80c02-122">Démarrez le composant logiciel enfichable MMC Services de composants.</span><span class="sxs-lookup"><span data-stu-id="80c02-122">Start the Component Services MMC snap-in.</span></span>  
  
    2.  <span data-ttu-id="80c02-123">Dans le composant logiciel enfichable MMC Services de composants, dans le volet gauche, développez **Services de composants**, développez **ordinateurs**, avec le bouton droit **poste**, puis cliquez sur  **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="80c02-123">In the Component Services MMC snap-in, from the left pane expand **Component Services**, expand **Computers**, right-click **My Computer**, and click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="80c02-124">Dans le **propriétés Poste de travail** boîte de dialogue, cliquez sur le **MSDTC** onglet.</span><span class="sxs-lookup"><span data-stu-id="80c02-124">In the **My Computer Properties** dialog box, click the **MSDTC** tab.</span></span>  
  
    4.  <span data-ttu-id="80c02-125">Dans le **Configuration de Transaction** , cliquez sur le **Configuration de la sécurité** bouton.</span><span class="sxs-lookup"><span data-stu-id="80c02-125">In the **Transaction Configuration** section, click the **Security Configuration** button.</span></span>  
  
    5.  <span data-ttu-id="80c02-126">Dans le **Configuration de la sécurité** boîte de dialogue, sélectionnez le **accès DTC réseau** et dans ce cas, cochez la **autoriser les Clients distants** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="80c02-126">In the **Security Configuration** dialog box, select the **Network DTC Access** check box and within that, select the **Allow Remote Clients** check box.</span></span>  
  
    6.  <span data-ttu-id="80c02-127">Dans le **Communication du Gestionnaire de transactions** section, sélectionnez le **autoriser les transactions entrantes** et **autoriser les transactions sortantes** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="80c02-127">In the **Transaction Manager Communication** section, select the **Allow Inbound** and **Allow Outbound** check boxes.</span></span>  
  
    7.  <span data-ttu-id="80c02-128">Dans le **Configuration de la sécurité** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80c02-128">In the **Security Configuration** dialog box, click **OK**.</span></span>  
  
    8.  <span data-ttu-id="80c02-129">Cliquez sur **Oui** dans la boîte dialogue informant que le service MSDTC doit être redémarré.</span><span class="sxs-lookup"><span data-stu-id="80c02-129">Click **Yes** in the dialog box informing that the MSDTC service will be restarted.</span></span> <span data-ttu-id="80c02-130">Une fois le service MSDTC est redémarré, cliquez sur **OK** sur la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="80c02-130">After the MSDTC service is restarted, click **OK** on the dialog box.</span></span>  
  
    9. <span data-ttu-id="80c02-131">Dans le **propriétés Poste de travail** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="80c02-131">In the **My Computer Properties** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="80c02-132">Ajouter de MSDTC à la liste d’exceptions de pare-feu Windows, si ce n’est pas déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="80c02-132">Add MSDTC to the Windows Firewall exception list, if not already added.</span></span> <span data-ttu-id="80c02-133">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="80c02-133">Run the following command.</span></span>  
  
    ```  
    netsh firewall set allowedprogram %windir%\system32\msdtc.exe MSDTC enable  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="80c02-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80c02-134">See Also</span></span>  
[<span data-ttu-id="80c02-135">Développer des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="80c02-135">Develop BizTalk applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)