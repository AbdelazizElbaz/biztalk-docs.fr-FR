---
title: Comment désactiver un mappage utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51c745dd-4d39-46e5-88bf-b803ae2e0a1b
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 93694ed8a3238be51b255bcad79122169461d885
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-disable-a-user-mapping"></a><span data-ttu-id="44198-102">Comment désactiver un mappage utilisateur</span><span class="sxs-lookup"><span data-stu-id="44198-102">How to Disable a User Mapping</span></span>
<span data-ttu-id="44198-103">Vous pouvez désactiver un mappage utilisateur pour désactiver les opérations qui lui sont associées.</span><span class="sxs-lookup"><span data-stu-id="44198-103">You can disable a user mapping when you want to turn off all operations associated with a given mapping.</span></span> <span data-ttu-id="44198-104">Vous devez désactiver un mappage utilisateur avant de le supprimer.</span><span class="sxs-lookup"><span data-stu-id="44198-104">You must disable a user mapping before you can remove it.</span></span>  
  
 <span data-ttu-id="44198-105">Lorsque vous désactivez un mappage utilisateur, il apparaît comme (D) *\<domaine >\\< nom d’utilisateur\>* lorsque vous répertoriez les mappages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44198-105">When you disable a user mapping, it will appear as (D) *\<domain>\\<username\>* when you list the user mappings.</span></span>  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a><span data-ttu-id="44198-106">Pour désactiver un mappage utilisateur à l'aide de l'utilitaire d'administration</span><span class="sxs-lookup"><span data-stu-id="44198-106">To disable a user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="44198-107">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="44198-107">Click **Start**, click **Run**, type `cmd`, and then press **ENTER**.</span></span>  
  
2.  <span data-ttu-id="44198-108">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="44198-108">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="44198-109">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="44198-109">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="44198-110">Type `ssomanage –disablemapping <domain>\<username><application name>`, où  *\<domaine >* correspond au domaine Windows pour le compte d’utilisateur,  *\<nom d’utilisateur >* est le nom d’utilisateur Windows pour lequel vous souhaitez désactiver le informations d’identification, et  *\<nom de l’application >* est le nom de l’application associée pour laquelle vous souhaitez supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44198-110">Type `ssomanage –disablemapping <domain>\<username><application name>`, where *\<domain>* is the Windows domain for the user account, *\<username>* is the Windows user name for which you want to disable the credentials, and *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.</span></span>  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="44198-111">Pour désactiver un mappage utilisateur à l'aide de l'utilitaire client</span><span class="sxs-lookup"><span data-stu-id="44198-111">To disable a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="44198-112">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="44198-112">Click **Start**, click **Run**, type `cmd`, and then press **ENTER**.</span></span>  
  
2.  <span data-ttu-id="44198-113">À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="44198-113">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="44198-114">Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.</span><span class="sxs-lookup"><span data-stu-id="44198-114">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="44198-115">Type `ssoclient –disablemapping <application name>`, où  *\<nom de l’application >* est le nom de l’application associée pour laquelle vous souhaitez supprimer le mappage utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44198-115">Type `ssoclient –disablemapping <application name>`, where *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44198-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44198-116">See Also</span></span>  
 <span data-ttu-id="44198-117">[Mappages SSO](../esso/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="44198-117">[SSO Mappings](../esso/sso-mappings.md) </span></span>  
 <span data-ttu-id="44198-118">[Gestion des Applications associées](../esso/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="44198-118">[Managing Affiliate Applications](../esso/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="44198-119">Gestion des mappages utilisateur</span><span class="sxs-lookup"><span data-stu-id="44198-119">Managing User Mappings</span></span>](../esso/managing-user-mappings.md)