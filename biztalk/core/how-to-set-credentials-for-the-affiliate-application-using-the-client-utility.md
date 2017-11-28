---
title: "Comment définir les informations d’identification de l’Application associée à l’aide de l’utilitaire Client | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], configuring credentials
- SSOClient [SSO], configuring credentials
- applications [SSO], credentials
ms.assetid: 454b6257-3538-40be-840c-00172a2c1dce
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31ba167bc35d01907166bb6610720e03be654c4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-credentials-for-the-affiliate-application-using-the-client-utility"></a><span data-ttu-id="7ca3f-102">Comment définir les informations d’identification de l’Application associée à l’aide de l’utilitaire Client</span><span class="sxs-lookup"><span data-stu-id="7ca3f-102">How to Set Credentials for the Affiliate Application Using the Client Utility</span></span>
<span data-ttu-id="7ca3f-103">Cette commande permet de définir les informations d'identification d'un utilisateur pour que celui-ci puisse accéder à une application spécifique.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-103">Use this command to set the credentials for a user so that the user is able to access a specific application.</span></span> <span data-ttu-id="7ca3f-104">Par ailleurs, elle active automatiquement le mappage.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-104">This command also automatically enables the mapping.</span></span>  
  
 <span data-ttu-id="7ca3f-105">Cette commande n'affiche pas le mot de passe durant sa saisie.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-105">This command does not display the password as you type it.</span></span>  
  
 <span data-ttu-id="7ca3f-106">Si le mappage utilisateur existe déjà, cette commande définit les informations d'identification pour le mappage existant.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-106">If the user mapping already exists, this command will set the credentials for that existing mapping.</span></span> <span data-ttu-id="7ca3f-107">Si vous n'avez pas créé le mappage utilisateur, le système SSO vous invite à saisir l'ID de l'utilisateur pour l'application.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-107">If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.</span></span>  
  
### <a name="to-set-credentials-for-the-affiliate-application-using-the-client-utility"></a><span data-ttu-id="7ca3f-108">Pour définir les informations d'identification de l'application associée à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="7ca3f-108">To set credentials for the affiliate application using the client utility</span></span>  
  
1.  <span data-ttu-id="7ca3f-109">Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-109">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="7ca3f-110">Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="7ca3f-111">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-111">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="7ca3f-112">Type **ssoclient – setcredentials \<nom de l’application >**, où  **\<nom de l’application >** est l’application spécifique pour lequel vous souhaitez définir les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-112">Type **ssoclient –setcredentials \<application name>**, where **\<application name>** is the specific application for which you want to set the credentials for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ca3f-113">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="7ca3f-114">Lorsque vous êtes invité à indiquer les informations d'identification de l'utilisateur, entrez le mot de passe pour cette application.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-114">When prompted for the user credentials, enter the user password for this application.</span></span>  
  
5.  <span data-ttu-id="7ca3f-115">Si vous n'avez pas créé le mappage utilisateur, le système SSO vous invite à saisir l'ID de l'utilisateur pour l'application.</span><span class="sxs-lookup"><span data-stu-id="7ca3f-115">If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca3f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ca3f-116">See Also</span></span>  
 <span data-ttu-id="7ca3f-117">[Applications associées SSO](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="7ca3f-117">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="7ca3f-118">Gestion des Applications associées</span><span class="sxs-lookup"><span data-stu-id="7ca3f-118">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)