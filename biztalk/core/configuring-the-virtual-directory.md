---
title: "Configuration du répertoire virtuel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directory, configuring
- configuring virtual directory
ms.assetid: 548e3bee-66bc-424c-895d-e8672a3d6301
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a879fe776956c290fb895c7f0feb39b6088e268
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-virtual-directory"></a><span data-ttu-id="5c8ad-102">Configuration du répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="5c8ad-102">Configuring the Virtual Directory</span></span>
<span data-ttu-id="5c8ad-103">Cette rubrique indique les procédures de configuration du répertoire virtuel et la vérification de l’application pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-103">This topic shows the procedures for configuring the virtual directory and verifying the application for a user.</span></span>  
  
## <a name="configuring-the-directory"></a><span data-ttu-id="5c8ad-104">Configuration du répertoire</span><span class="sxs-lookup"><span data-stu-id="5c8ad-104">Configuring the Directory</span></span>  
  
#### <a name="to-configure-the-virtual-directory"></a><span data-ttu-id="5c8ad-105">Pour configurer le répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="5c8ad-105">To configure the virtual directory</span></span>  
  
1.  <span data-ttu-id="5c8ad-106">Sur le lecteur système (%systemdrive%), créez un dossier à configurer en tant que répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-106">On the %systemdrive%, create a folder to be configured as a virtual directory.</span></span>  
  
2.  <span data-ttu-id="5c8ad-107">Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-107">Click **Start**, point to **Programs**, click **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span>  
  
3.  <span data-ttu-id="5c8ad-108">Développez  **\<nom du serveur >** , puis **Sites**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-108">Expand **\<server name>** and then expand **Sites**.</span></span>  
  
4.  <span data-ttu-id="5c8ad-109">Avec le bouton droit **Site Web par défaut** et cliquez sur **ajouter un répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-109">Right-click **Default Web Site** and click **Add Virtual Directory**.</span></span>  
  
5.  <span data-ttu-id="5c8ad-110">Dans le **ajouter un répertoire virtuel** boîte de dialogue, tapez l’alias.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-110">In the **Add Virtual Directory** dialog box, type the alias.</span></span>  
  
6.  <span data-ttu-id="5c8ad-111">Tapez le chemin d'accès au dossier créé à l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-111">Type the path of the folder created in step 1.</span></span> <span data-ttu-id="5c8ad-112">Sinon, cliquez sur **(...)**  pour accéder à l’emplacement du dossier.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-112">Alternatively, click **(…)** to browse to the folder location.</span></span>  
  
7.  <span data-ttu-id="5c8ad-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-113">Click **OK**.</span></span> <span data-ttu-id="5c8ad-114">Le dossier s’affiche sous le **Site Web par défaut** dossier.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-114">The folder is displayed under the **Default Web Site** folder.</span></span>  
  
8.  <span data-ttu-id="5c8ad-115">Cliquez avec le bouton droit et cliquez sur **convertir en Application**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-115">Right-click the folder and click **Convert to Application**.</span></span>  
  
9. <span data-ttu-id="5c8ad-116">Dans le **ajouter une Application** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-116">In the **Add Application** dialog box, click **OK**.</span></span> <span data-ttu-id="5c8ad-117">Le dossier est converti en application (l'icône de dossier devient une icône de site Web).</span><span class="sxs-lookup"><span data-stu-id="5c8ad-117">The folder is converted to an application (you can see the change in the icon – from a folder icon to the Web site icon).</span></span>  
  
## <a name="verifying-an-application-for-a-user"></a><span data-ttu-id="5c8ad-118">Vérification d'une application pour un utilisateur</span><span class="sxs-lookup"><span data-stu-id="5c8ad-118">Verifying an Application for a User</span></span>  
 <span data-ttu-id="5c8ad-119">Les applications IIS sont exécutées à un niveau d'isolation élevé. Aussi, vous devez vérifier que l'application peut être exécutée dans le contexte d'un utilisateur dans le groupe Utilisateurs d'hôtes BizTalk isolés à l'aide de la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-119">Internet Information Services (IIS) applications run in high isolation; therefore, you must verify that the application can run in the context of a user in the BizTalk Server Isolated Host Users group by using the following procedure.</span></span>  
  
#### <a name="to-verify-an-application-for-a-user"></a><span data-ttu-id="5c8ad-120">Pour vérifier une application pour un utilisateur</span><span class="sxs-lookup"><span data-stu-id="5c8ad-120">To verify an application for a user</span></span>  
  
1.  <span data-ttu-id="5c8ad-121">Dans le panneau de configuration, ouvrez **outils d’administration**, puis cliquez sur **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-121">In Control Panel, open **Administrative Tools**, and then click **Component Services**.</span></span>  
  
2.  <span data-ttu-id="5c8ad-122">Accédez à l’application COM + dans **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-122">Navigate to the COM+ application in **Component Services**.</span></span>  
  
3.  <span data-ttu-id="5c8ad-123">Cliquez sur l’application COM +, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-123">Right-click the COM+ application, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5c8ad-124">Cliquez sur **identifier** et modifier l’identité sous laquelle cette application COM + s’exécute à un utilisateur qui est membre d’un groupe BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5c8ad-124">Click **Identify** and change the identity under which this COM+ application runs to a user that is a member of a BizTalk Server group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8ad-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c8ad-125">See Also</span></span>  
 [<span data-ttu-id="5c8ad-126">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="5c8ad-126">Using Single Sign-On</span></span>](../core/using-single-sign-on3.md)