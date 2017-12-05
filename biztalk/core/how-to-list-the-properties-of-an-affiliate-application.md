---
title: "Comment afficher les propriétés d’une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], listing properties
- managing [SSO applications], listing properties
ms.assetid: a120acd7-2f0b-4c72-8a8a-f8e500a773c8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3ac0c77dbaad27012f104486797c4e47d1e46be
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a><span data-ttu-id="827ea-102">Comment afficher les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="827ea-102">How to List the Properties of an Affiliate Application</span></span>
<span data-ttu-id="827ea-103">Cette commande affiche les informations suivantes sur l'application associée.</span><span class="sxs-lookup"><span data-stu-id="827ea-103">This command shows the following information about the affiliate application.</span></span> <span data-ttu-id="827ea-104">Pour plus d’informations sur les propriétés d’une application associée, consultez [Applications associées SSO](../core/sso-affiliate-applications.md).</span><span class="sxs-lookup"><span data-stu-id="827ea-104">For more information about the properties for an affiliate application, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).</span></span>  
  
 <span data-ttu-id="827ea-105">Le système d'authentification unique tire ces informations du fichier xml que vous avez utilisé pour mettre à jour l'application affiliée.</span><span class="sxs-lookup"><span data-stu-id="827ea-105">The SSO system obtains this information from the xml file that you used to update the affiliate application.</span></span> <span data-ttu-id="827ea-106">Pour plus d’informations, consultez [comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md).</span><span class="sxs-lookup"><span data-stu-id="827ea-106">For more information, see [How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md).</span></span>  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a><span data-ttu-id="827ea-107">Pour afficher les propriétés d'une application affiliée à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="827ea-107">To display the properties of an affiliate application using the administration utility</span></span>  
  
1.  <span data-ttu-id="827ea-108">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="827ea-108">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="827ea-109">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="827ea-109">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="827ea-110">Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="827ea-110">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="827ea-111">Type **ssomanage-displayapp  *\<nom de l’application\>***, où  *\<nom de l’application\>*  est le nom de l’Application associée que vous souhaitez afficher les propriétés.</span><span class="sxs-lookup"><span data-stu-id="827ea-111">Type **ssomanage –displayapp *\<application name\>***, where *\<application name\>* is the name of the Affiliate Application you want to display the properties for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="827ea-112">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="827ea-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a><span data-ttu-id="827ea-113">Pour afficher les propriétés d'une application affiliée à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="827ea-113">To display the properties of an affiliate application using the client utility</span></span>  
  
1.  <span data-ttu-id="827ea-114">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="827ea-114">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="827ea-115">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="827ea-115">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="827ea-116">Le répertoire d’installation par défaut est \< *lecteur d’installation*\>: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="827ea-116">The default installation directory is \<*install drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="827ea-117">Type **ssoclient – displayapp  *\<nom de l’application\>***, où  *\<nom de l’application\>*  est le nom de l’Application associée que vous souhaitez afficher les propriétés.</span><span class="sxs-lookup"><span data-stu-id="827ea-117">Type **ssoclient –displayapp *\<application name\>***, where *\<application name\>* is the name of the Affiliate Application you want to display the properties for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="827ea-118">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="827ea-118">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827ea-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="827ea-119">See Also</span></span>  
 <span data-ttu-id="827ea-120">[Gestion des mappages utilisateur](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="827ea-120">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="827ea-121">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="827ea-121">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)