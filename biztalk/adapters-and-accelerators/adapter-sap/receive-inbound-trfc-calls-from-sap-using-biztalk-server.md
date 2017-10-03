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
# <a name="receive-inbound-trfc-calls-from-sap-using-biztalk-server"></a><span data-ttu-id="d6d55-102">Réception entrant tRFC appelle à partir de SAP à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d6d55-102">Receive Inbound tRFC Calls from SAP using BizTalk Server</span></span>
<span data-ttu-id="d6d55-103">Un appel de serveur tRFC est un appel de serveur RFC transactionnels.</span><span class="sxs-lookup"><span data-stu-id="d6d55-103">A tRFC server call is a transactional RFC server call.</span></span> <span data-ttu-id="d6d55-104">L’orchestration permet de recevoir une commande RFC dans un contexte transactionnel est similaire à l’orchestration de recevoir toutes les autres RFC entrant envoyé à partir d’un système SAP.</span><span class="sxs-lookup"><span data-stu-id="d6d55-104">The orchestration required to receive an RFC in a transactional context is similar to the orchestration to receive any other inbound RFC sent from an SAP system.</span></span> <span data-ttu-id="d6d55-105">Toutefois, vous devez effectuer certaines tâches supplémentaires pour vous assurer que les documents RFC sont reçus dans un contexte transactionnel.</span><span class="sxs-lookup"><span data-stu-id="d6d55-105">However, you need to perform certain additional tasks to make sure the RFCs are received in a transactional context.</span></span> <span data-ttu-id="d6d55-106">Pour plus d’informations sur la réception d’une demande de changement de trafic entrant du système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [recevoir les appels RFC entrants à partir de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="d6d55-106">For more information about receiving an inbound RFC from the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Receive Inbound RFC Calls from SAP by using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md).</span></span> <span data-ttu-id="d6d55-107">Pour plus d’informations sur la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge de recevoir des appels de tRFC entrant à partir d’un système SAP, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span><span class="sxs-lookup"><span data-stu-id="d6d55-107">For more information about how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports receiving inbound tRFC calls from an SAP system, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
 <span data-ttu-id="d6d55-108">Réception d’un tRFC entrant envoyé à partir d’un système SAP est similaire à la réception d’une commande RFC entrante, avec les différences suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6d55-108">Receiving an inbound tRFC sent from an SAP system is similar to receiving an inbound RFC, with the following differences:</span></span>  
  
1.  <span data-ttu-id="d6d55-109">Au moment du design, lors de la génération du schéma, veillez à sélectionner le tRFC sous le **TRFC** nœud.</span><span class="sxs-lookup"><span data-stu-id="d6d55-109">At design time, while generating the schema, make sure you select the tRFC from under the **TRFC** node.</span></span>  
  
2.  <span data-ttu-id="d6d55-110">Au moment de l’exécution, assurez-vous que vous définissez la propriété binding **TidDatabaseConnectionString**.</span><span class="sxs-lookup"><span data-stu-id="d6d55-110">At run time, make sure you set the binding property **TidDatabaseConnectionString**.</span></span> <span data-ttu-id="d6d55-111">Cette propriété prend la chaîne de connexion pour se connecter à une base de données SQL pour stocker le TID.</span><span class="sxs-lookup"><span data-stu-id="d6d55-111">This property takes the connection string to connect to a SQL database to store the TID.</span></span> <span data-ttu-id="d6d55-112">Un exemple de chaîne de connexion ressemble à :</span><span class="sxs-lookup"><span data-stu-id="d6d55-112">A sample connection string would look like:</span></span>  
  
    ```  
    Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;  
    ```  
  
     <span data-ttu-id="d6d55-113">Pour plus d’informations sur la propriété de liaison et comment le configurer, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d6d55-113">For more information about the binding property and how to set it, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d6d55-114">Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Assistant Installation installe SQL script, SapAdapter-DbScript-Install.sql, qui doit être exécutée par l’administrateur SQL Server pour créer une base de données et les objets de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d6d55-114">The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard installs a SQL script, SapAdapter-DbScript-Install.sql, which must be run by the SQL Server administrator to create a database and the database objects in SQL Server.</span></span> <span data-ttu-id="d6d55-115">Le script est généralement installé sur  *\<lecteur d’installation > : programme FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]* .</span><span class="sxs-lookup"><span data-stu-id="d6d55-115">The script is typically installed at *\<installation drive>:Program FilesMicrosoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]*.</span></span>  
    >   
    >  <span data-ttu-id="d6d55-116">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise ces objets pour conserver le TID.</span><span class="sxs-lookup"><span data-stu-id="d6d55-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses these objects to persist the TIDs.</span></span> <span data-ttu-id="d6d55-117">Par conséquent, l’administrateur SQL Server devez vous assurer que le nom d’utilisateur assure que la partie de la chaîne de connexion dispose des privilèges suffisants pour exécuter les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="d6d55-117">So, the SQL Server administrator must ensure that the user name provide as part of the connection string has sufficient privileges to execute the stored procedures.</span></span> <span data-ttu-id="d6d55-118">Vous pouvez également choisir pour l’authentification Windows à condition que l’utilisateur Windows dispose des autorisations suffisantes pour exécuter des procédures stockées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="d6d55-118">You can also opt for Windows authentication provided the Windows user has sufficient permissions to execute stored procedures in the database.</span></span>  
  
3.  <span data-ttu-id="d6d55-119">Vérifiez que MSDTC est activé sur l’ordinateur sur lequel l’adaptateur est installé.</span><span class="sxs-lookup"><span data-stu-id="d6d55-119">Make sure MSDTC is enabled on the computer where the adapter is installed.</span></span> <span data-ttu-id="d6d55-120">Procédez comme suit pour activer le service MSDTC.</span><span class="sxs-lookup"><span data-stu-id="d6d55-120">Perform the following steps to enable MSDTC.</span></span>  
  
    1.  <span data-ttu-id="d6d55-121">Démarrez le composant logiciel enfichable MMC Services de composants.</span><span class="sxs-lookup"><span data-stu-id="d6d55-121">Start the Component Services MMC snap-in.</span></span>  
  
    2.  <span data-ttu-id="d6d55-122">Dans le composant logiciel enfichable MMC Services de composants, dans le volet gauche, développez **Services de composants**, développez **ordinateurs**, avec le bouton droit **poste**, puis cliquez sur  **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d6d55-122">In the Component Services MMC snap-in, from the left pane expand **Component Services**, expand **Computers**, right-click **My Computer**, and click **Properties**.</span></span>  
  
    3.  <span data-ttu-id="d6d55-123">Dans le **propriétés Poste de travail** boîte de dialogue, cliquez sur le **MSDTC** onglet.</span><span class="sxs-lookup"><span data-stu-id="d6d55-123">In the **My Computer Properties** dialog box, click the **MSDTC** tab.</span></span>  
  
    4.  <span data-ttu-id="d6d55-124">Dans le **Configuration de Transaction** , cliquez sur le **Configuration de la sécurité** bouton.</span><span class="sxs-lookup"><span data-stu-id="d6d55-124">In the **Transaction Configuration** section, click the **Security Configuration** button.</span></span>  
  
    5.  <span data-ttu-id="d6d55-125">Dans le **Configuration de la sécurité** boîte de dialogue, sélectionnez le **accès DTC réseau** et dans ce cas, cochez la **autoriser les Clients distants** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="d6d55-125">In the **Security Configuration** dialog box, select the **Network DTC Access** check box and within that, select the **Allow Remote Clients** check box.</span></span>  
  
    6.  <span data-ttu-id="d6d55-126">Dans le **Communication du Gestionnaire de transactions** section, sélectionnez le **autoriser les transactions entrantes** et **autoriser les transactions sortantes** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="d6d55-126">In the **Transaction Manager Communication** section, select the **Allow Inbound** and **Allow Outbound** check boxes.</span></span>  
  
    7.  <span data-ttu-id="d6d55-127">Dans le **Configuration de la sécurité** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d6d55-127">In the **Security Configuration** dialog box, click **OK**.</span></span>  
  
    8.  <span data-ttu-id="d6d55-128">Cliquez sur **Oui** dans la boîte dialogue informant que le service MSDTC doit être redémarré.</span><span class="sxs-lookup"><span data-stu-id="d6d55-128">Click **Yes** in the dialog box informing that the MSDTC service will be restarted.</span></span> <span data-ttu-id="d6d55-129">Une fois le service MSDTC est redémarré, cliquez sur **OK** sur la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d6d55-129">After the MSDTC service is restarted, click **OK** on the dialog box.</span></span>  
  
    9. <span data-ttu-id="d6d55-130">Dans le **propriétés Poste de travail** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d6d55-130">In the **My Computer Properties** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="d6d55-131">Ajouter de MSDTC à la liste d’exceptions de pare-feu Windows, si ce n’est pas déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="d6d55-131">Add MSDTC to the Windows Firewall exception list, if not already added.</span></span> <span data-ttu-id="d6d55-132">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d6d55-132">Run the following command.</span></span>  
  
    ```  
    netsh firewall set allowedprogram %windir%\system32\msdtc.exe MSDTC enable  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="d6d55-133">Un appel entrant tRFC est utilisé lors de la réception des IDOC à partir du système SAP dans un contexte « transactionnel ».</span><span class="sxs-lookup"><span data-stu-id="d6d55-133">An inbound tRFC call is used while receiving IDOCs from the SAP system in a "transactional" context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d55-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6d55-134">See Also</span></span>  
[<span data-ttu-id="d6d55-135">Développer des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="d6d55-135">Develop BizTalk applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)