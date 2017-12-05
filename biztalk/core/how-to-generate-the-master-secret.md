---
title: "Comment générer le Secret | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, generating
- managing [Master Secret server], generating
ms.assetid: 5512a8ee-bc5b-4fe4-90c7-41e3baaa723b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1a7ee4f8ffe73a71e8c0b2e3d45c7a966669fd8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-generate-the-master-secret"></a><span data-ttu-id="180d8-102">Comment générer le Secret principal</span><span class="sxs-lookup"><span data-stu-id="180d8-102">How to Generate the Master Secret</span></span>
<span data-ttu-id="180d8-103">Vous devez disposer de droits d'administrateur sur le serveur de secret principal pour effectuer cette tâche.</span><span class="sxs-lookup"><span data-stu-id="180d8-103">You must have administrator rights on the master secret server in order to perform this task.</span></span> <span data-ttu-id="180d8-104">Par ailleurs, vous devez effectuer cette tâche depuis le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="180d8-104">In addition, you must perform this task from the master secret server.</span></span>  
  
 <span data-ttu-id="180d8-105">Le premier serveur sur lequel vous installez l'authentification unique de l'entreprise (SSO) devient le serveur de secret principal.</span><span class="sxs-lookup"><span data-stu-id="180d8-105">The first server where you install Enterprise Single Sign-On becomes the master secret server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="180d8-106">Il ne peut y avoir qu'un serveur de secret principal dans votre système SSO.</span><span class="sxs-lookup"><span data-stu-id="180d8-106">There can be only one master secret server in your SSO system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="180d8-107">Lorsque l'authentification unique de l'entreprise est installée en même temps que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le secret principal est généré via l'Assistant Configuration.</span><span class="sxs-lookup"><span data-stu-id="180d8-107">When Enterprise Single Sign-On is installed as part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation, the master secret is generated as part of the Configuration Wizard.</span></span> <span data-ttu-id="180d8-108">Vous ne devez effectuer cette tâche que si vous souhaitez générer un nouveau secret principal.</span><span class="sxs-lookup"><span data-stu-id="180d8-108">You will only need to perform this task if you want to generate a new master secret.</span></span>  
  
### <a name="to-generate-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="180d8-109">Pour générer le secret principal à l'aide du composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="180d8-109">To generate the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="180d8-110">Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.</span><span class="sxs-lookup"><span data-stu-id="180d8-110">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="180d8-111">Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .</span><span class="sxs-lookup"><span data-stu-id="180d8-111">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="180d8-112">Avec le bouton droit **système**, puis cliquez sur **générer le Secret**.</span><span class="sxs-lookup"><span data-stu-id="180d8-112">Right-click **System**, and then click **Generate Secret**.</span></span>  
  
### <a name="to-generate-the-master-secret-using-the-command-line"></a><span data-ttu-id="180d8-113">Pour générer le secret principal à l'aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="180d8-113">To generate the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="180d8-114">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="180d8-114">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="180d8-115">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="180d8-115">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="180d8-116">Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="180d8-116">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="180d8-117">Type  **ssoconfig – generateSecret \<* fichier de sauvegarde*\>**, où \<* le fichier de sauvegarde* \> est le nom du fichier qui contient le secret principal.</span><span class="sxs-lookup"><span data-stu-id="180d8-117">Type **ssoconfig –generateSecret \<*backup file*\>**, where \<*backup file*\> is the name of the file that contains the master secret.</span></span>  
  
     <span data-ttu-id="180d8-118">Vous êtes ensuite invité à entrer un mot de passe pour protéger le fichier que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="180d8-118">You will be prompted to enter a password to protect the file you just created.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="180d8-119">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="180d8-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="180d8-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="180d8-120">See Also</span></span>  
 <span data-ttu-id="180d8-121">[Comment sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="180d8-121">[How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md) </span></span>  
 <span data-ttu-id="180d8-122">[Serveur de secret principal](../core/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="180d8-122">[Master Secret Server](../core/master-secret-server.md) </span></span>  
 [<span data-ttu-id="180d8-123">Gestion du secret principal</span><span class="sxs-lookup"><span data-stu-id="180d8-123">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)