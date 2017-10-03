---
title: "Comment créer un adaptateur WCF pour BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ddaeb72-d263-4291-bd79-485fc736e6e7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebe1bbb9282db88f1b4370cea4b59ff4fcbfe6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-wcf-adapter-for-biztalk-server"></a><span data-ttu-id="8fb7d-102">Comment créer un adaptateur WCF pour BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8fb7d-102">How to Create a WCF Adapter for BizTalk Server</span></span>
<span data-ttu-id="8fb7d-103">La création d'un adaptateur [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] BizTalk s'effectue en trois étapes.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-103">There are three parts to creating a BizTalk [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] adapter.</span></span>  
  
-   <span data-ttu-id="8fb7d-104">Créez un service Web [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] à l'aide de l'Assistant Publication de services [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-104">Create a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Web service using the BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Publishing Wizard.</span></span> <span data-ttu-id="8fb7d-105">Pour plus d’informations sur l’utilisation de BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Assistant Publication de services, consultez [publication des Services WCF](../core/publishing-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8fb7d-105">For information about using the BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Publishing Wizard, see [Publishing WCF Services](../core/publishing-wcf-services.md).</span></span>  
  
-   <span data-ttu-id="8fb7d-106">Configurez des emplacements et ports de réception et d'envoi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8fb7d-106">Configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive and send locations and ports by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="8fb7d-107">Pour obtenir un exemple de procédure à suivre, consultez [comment configurer recevoir et envoyer des emplacements et Ports pour l’Interception de BAM WCF](../core/how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception.md).</span><span class="sxs-lookup"><span data-stu-id="8fb7d-107">For an example of how to do this, see [How to Configure Receive and Send Locations and Ports for BAM WCF Interception](../core/how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception.md).</span></span>  
  
-   <span data-ttu-id="8fb7d-108">Si vous hébergez votre solution dans IIS, vous devez configurer le service Web [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] à l'aide du Gestionnaire des services Internet.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-108">If you are hosting your solution in IIS, you must configure the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Web service by using IIS Manager.</span></span>  
  
    -   <span data-ttu-id="8fb7d-109">Vous devez accorder des autorisations à l'utilisateur du pool d'applications.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-109">You must grant permissions to the App pool user.</span></span> <span data-ttu-id="8fb7d-110">Pour ce faire, consultez [considérations de sécurité pour l’emprunt d’identité IIS](../core/security-considerations-for-iis-impersonation.md).</span><span class="sxs-lookup"><span data-stu-id="8fb7d-110">To do this, see [Security Considerations for IIS Impersonation](../core/security-considerations-for-iis-impersonation.md).</span></span>  
  
    -   <span data-ttu-id="8fb7d-111">Vous devez définir la sécurité de répertoire pour votre application, comme décrit dans la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-111">You must set the directory security for your application as described in the following procedure.</span></span>  
  
## <a name="setting-the-directory-security"></a><span data-ttu-id="8fb7d-112">Configuration de la sécurité de répertoire</span><span class="sxs-lookup"><span data-stu-id="8fb7d-112">Setting the Directory Security</span></span>  
 <span data-ttu-id="8fb7d-113">Vérifiez que le contrôle d'accès à la sécurité de répertoire pour le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] autorise l'accès anonyme. Ceci simplifie l'accès à l'application.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-113">Ensure that the Directory Security Access Control for the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service allows for anonymous access; this simplifies the application access.</span></span>  
  
 <span data-ttu-id="8fb7d-114">Par exemple, si votre application est nommée MyBizTalkService3 et que le site Web MyBizTalkService3 fait partie des sites Web par défaut, suivez cette procédure pour définir le contrôle d'accès.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-114">For example, if your application is named MyBizTalkService3 and you have a MyBizTalkService3 that is in Default Websites, you would follow this procedure to set the access control.</span></span>  
  
#### <a name="to-set-the-access-control-in-windows-server-2008"></a><span data-ttu-id="8fb7d-115">Pour définir le contrôle d'accès dans Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="8fb7d-115">To set the access control in Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="8fb7d-116">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, développez **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-116">Click **Start**, click **All Programs**, expand **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="8fb7d-117">Dans la fenêtre Gestionnaire des Services Internet (IIS), développez le nom de votre serveur, **Sites**, développez **Internet Information Services**, puis développez **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-117">In the Internet Information Services (IIS) Manager window, expand your server name, expand **Sites**, expand **Internet Information Services**, and then expand **Default Web Site**.</span></span>  
  
3.  <span data-ttu-id="8fb7d-118">Avec le bouton droit **MyBizTalkService3**, puis cliquez sur **modifier les autorisations**.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-118">Right-click **MyBizTalkService3**, and then click **Edit Permissions**.</span></span>  
  
4.  <span data-ttu-id="8fb7d-119">Sur le **sécurité** onglet de la **propriétés de MyBizTalkService3** boîte de dialogue, cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-119">On the **Security** tab of the **MyBizTalkService3 Properties** dialog box, click **Edit**.</span></span>  
  
5.  <span data-ttu-id="8fb7d-120">Dans le **autorisations de MyBizTalkService3** boîte de dialogue, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-120">In the **Permissions for MyBizTalkService3** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="8fb7d-121">Dans le **sélectionnez utilisateurs, ordinateurs ou groupes** boîte de dialogue, tapez `anonymous logon` puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-121">In the **Select Users, Computers, or Groups** dialog box, type `anonymous logon` and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="8fb7d-122">Sélectionnez **ouverture de session anonyme** dans le **noms d’utilisateur ou groupe** section, sélectionnez **en lecture & exécution** dans le **autorisations d’ouverture de session anonyme** section, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-122">Select **ANONYMOUS LOGON** in the **Group or user names** section, select **Read & execute** in the **Permissions for ANONYMOUS LOGON** section, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="8fb7d-123">Cliquez sur **OK** pour fermer la **propriétés de MyBizTalkService3** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-123">Click **OK** to close the **MyBizTalkService3 Properties** dialog box.</span></span>  
  
 <span data-ttu-id="8fb7d-124">Pour confirmer que le service est correctement configuré, cliquez sur le service, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-124">To confirm that the service is configured correctly, right-click the service, and then click **Browse**.</span></span>  
  
 <span data-ttu-id="8fb7d-125">Si le service est correctement configuré, une page semblable à la suivante est affichée.</span><span class="sxs-lookup"><span data-stu-id="8fb7d-125">If the service is configured correctly, you will see a screen similar to the one below.</span></span>  
  
 <span data-ttu-id="8fb7d-126">![Écran du Service BizTalkServiceInstance](../core/media/ff0e4ba0-59e7-47d9-a252-2859179f5645.gif "ff0e4ba0-59e7-47d9-a252-2859179f5645")</span><span class="sxs-lookup"><span data-stu-id="8fb7d-126">![BizTalkServiceInstance Service Screen](../core/media/ff0e4ba0-59e7-47d9-a252-2859179f5645.gif "ff0e4ba0-59e7-47d9-a252-2859179f5645")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb7d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fb7d-127">See Also</span></span>  
 [<span data-ttu-id="8fb7d-128">Configuration de l’adaptateur WCF pour intercepter les données BAM</span><span class="sxs-lookup"><span data-stu-id="8fb7d-128">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)