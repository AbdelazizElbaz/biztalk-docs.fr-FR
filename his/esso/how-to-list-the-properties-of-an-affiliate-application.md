---
title: Comment afficher les propriétés d’une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fac15775-39d0-470e-b9d2-21b2d02e1de7
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: e35f1f068f63d4db9738733bcada55047e81a19a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a><span data-ttu-id="979b2-102">Comment afficher les propriétés d’une Application associée</span><span class="sxs-lookup"><span data-stu-id="979b2-102">How to List the Properties of an Affiliate Application</span></span>
<span data-ttu-id="979b2-103">Le **displayapp** commande affiche les informations suivantes sur l’application associée.</span><span class="sxs-lookup"><span data-stu-id="979b2-103">The **displayapp** command shows the following information about the affiliate application.</span></span> <span data-ttu-id="979b2-104">Pour plus d’informations sur les propriétés d’une application associée, consultez [Applications associées SSO](../esso/sso-affiliate-applications.md).</span><span class="sxs-lookup"><span data-stu-id="979b2-104">For more information about the properties for an affiliate application, see [SSO Affiliate Applications](../esso/sso-affiliate-applications.md).</span></span>  
  
 <span data-ttu-id="979b2-105">Le système Single Sign-On (SSO) obtient ces informations à partir du fichier XML que vous avez utilisé pour mettre à jour de l’application associée.</span><span class="sxs-lookup"><span data-stu-id="979b2-105">The Single Sign-On (SSO) system obtains this information from the XML file that you used to update the affiliate application.</span></span> <span data-ttu-id="979b2-106">Pour plus d’informations, consultez [comment mettre à jour les propriétés d’une Application associée](../esso/how-to-update-the-properties-of-an-affiliate-application.md).</span><span class="sxs-lookup"><span data-stu-id="979b2-106">For more information, see [How to Update the Properties of an Affiliate Application](../esso/how-to-update-the-properties-of-an-affiliate-application.md).</span></span>  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a><span data-ttu-id="979b2-107">Pour afficher les propriétés d'une application affiliée à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="979b2-107">To display the properties of an affiliate application using the administration utility</span></span>  
  
1.  <span data-ttu-id="979b2-108">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="979b2-108">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="979b2-109">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="979b2-109">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="979b2-110">Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="979b2-110">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="979b2-111">Type `ssomanage –displayapp <application name>`, où  *\<nom de l’application >* est le nom de l’application associée que vous souhaitez afficher les propriétés.</span><span class="sxs-lookup"><span data-stu-id="979b2-111">Type `ssomanage –displayapp <application name>`, where *\<application name>* is the name of the affiliate application that you want to display the properties for.</span></span>  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a><span data-ttu-id="979b2-112">Pour afficher les propriétés d'une application affiliée à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="979b2-112">To display the properties of an affiliate application using the client utility</span></span>  
  
1.  <span data-ttu-id="979b2-113">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="979b2-113">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="979b2-114">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="979b2-114">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="979b2-115">Le répertoire d’installation par défaut est \< *lecteur d’installation*> : \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="979b2-115">The default installation directory is \<*install drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="979b2-116">Type `ssoclient –displayapp <application name>`, où  *\<nom de l’application >* est le nom de l’application associée que vous souhaitez afficher les propriétés.</span><span class="sxs-lookup"><span data-stu-id="979b2-116">Type `ssoclient –displayapp <application name>`, where *\<application name>* is the name of the affiliate application that you want to display the properties for.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979b2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="979b2-117">See Also</span></span>  
 <span data-ttu-id="979b2-118">[Gestion des mappages utilisateur](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="979b2-118">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="979b2-119">Gestion des applications associées</span><span class="sxs-lookup"><span data-stu-id="979b2-119">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)