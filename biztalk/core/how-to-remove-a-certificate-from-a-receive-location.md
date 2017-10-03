---
title: "Comment supprimer un certificat d’un emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, receive locations
- receive locations, certificates
- managing [receive locations], certificates
ms.assetid: 717d41bf-4260-4df4-9d0a-07243bb9b12c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e70cd846c364d52544bf8504d42132dd35fe65d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-certificate-from-a-receive-location"></a><span data-ttu-id="a8708-102">Suppression d'un certificat d'un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="a8708-102">How to Remove a Certificate from a Receive Location</span></span>
<span data-ttu-id="a8708-103">Cette rubrique décrit comment supprimer un certificat de sécurité d'un emplacement de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a8708-103">This topic describes how to use the BizTalk Server Administration console to remove a security certificate from a receive location.</span></span> <span data-ttu-id="a8708-104">Une fois cette opération effectuée, l'emplacement de réception ne chiffrera plus les messages. Ils seront désormais envoyés en texte clair.</span><span class="sxs-lookup"><span data-stu-id="a8708-104">When you do this, the receive location will no longer encrypt messages; messages will be sent in clear text.</span></span> <span data-ttu-id="a8708-105">Supprimer un certificat d'un emplacement de réception ne le supprime pas automatiquement du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="a8708-105">Removing a certificate from a receive location does not remove it from the certificate store.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8708-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a8708-106">Prerequisites</span></span>  
 <span data-ttu-id="a8708-107">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a8708-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="a8708-108">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="a8708-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-certificate-from-a-receive-location"></a><span data-ttu-id="a8708-109">Pour supprimer un certificat d'un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="a8708-109">To remove a certificate from a receive location</span></span>  
  
1.  <span data-ttu-id="a8708-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a8708-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a8708-111">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend l'emplacement de réception dans lequel supprimer un certificat.</span><span class="sxs-lookup"><span data-stu-id="a8708-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to remove a certificate from a receive location.</span></span>  
  
3.  <span data-ttu-id="a8708-112">Développez **emplacements de réception**, avec le bouton droit à l’emplacement de réception, cliquez sur **propriétés**, puis cliquez sur **certificats**.</span><span class="sxs-lookup"><span data-stu-id="a8708-112">Expand **Receive Locations**, right-click the receive location, click **Properties**, and then click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="a8708-113">Cliquez sur **supprimer le certificat**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8708-113">Click **Remove certificate**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8708-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8708-114">See Also</span></span>  
 [<span data-ttu-id="a8708-115">La gestion des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="a8708-115">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)