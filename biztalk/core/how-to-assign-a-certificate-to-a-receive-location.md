---
title: "Comment attribuer un certificat à un emplacement de réception | Documents Microsoft"
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
ms.assetid: 54ae300e-62c5-480f-a9b7-e5c3457a0f80
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94554aa5781ed609e5129d58ab75e5709e432278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-a-certificate-to-a-receive-location"></a><span data-ttu-id="aee3c-102">Attribution d'un certificat à un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="aee3c-102">How to Assign a Certificate to a Receive Location</span></span>
<span data-ttu-id="aee3c-103">Cette rubrique décrit comment attribuer un certificat de sécurité à un emplacement de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="aee3c-103">This topic describes how to use the BizTalk Server Administration console to assign a security certificate to a receive location.</span></span> <span data-ttu-id="aee3c-104">Cette procédure n'est possible que sur les emplacements de réception bidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="aee3c-104">You can perform this procedure on a two-way receive location only.</span></span> <span data-ttu-id="aee3c-105">Le certificat doit figurer dans le magasin de certificats Autres personnes sur l'ordinateur exécutant BizTalk Server, faute de quoi les messages associés à cet emplacement de réception ne seront pas traités et des erreurs seront consignées.</span><span class="sxs-lookup"><span data-stu-id="aee3c-105">The certificate must exist in the Other People certificate store on the computer running BizTalk Server, or messages associated with this receive location will not be processed, and errors will be logged.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aee3c-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="aee3c-106">Prerequisites</span></span>  
 <span data-ttu-id="aee3c-107">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="aee3c-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="aee3c-108">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="aee3c-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-assign-a-certificate-to-a-receive-location"></a><span data-ttu-id="aee3c-109">Pour attribuer un certificat à un emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="aee3c-109">To assign a certificate to a receive location</span></span>  
  
1.  <span data-ttu-id="aee3c-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="aee3c-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="aee3c-111">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle attribuer un certificat à un emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="aee3c-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to assign a certificate to a receive location.</span></span>  
  
3.  <span data-ttu-id="aee3c-112">Développez **emplacements de réception**, avec le bouton droit à l’emplacement de réception, cliquez sur **propriétés**, puis cliquez sur **certificat**.</span><span class="sxs-lookup"><span data-stu-id="aee3c-112">Expand **Receive Locations**, right-click the receive location, click **Properties**, and then click **Certificate**.</span></span>  
  
4.  <span data-ttu-id="aee3c-113">Si le certificat existe sur l’ordinateur local, cliquez sur **Parcourir**, localisez le certificat que vous souhaitez attribuer à cet emplacement de réception et puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aee3c-113">If the certificate exists on the local computer, click **Browse**, browse to the certificate that you want to assign to this receive location, and then click **OK**.</span></span> <span data-ttu-id="aee3c-114">Sinon, ignorez cette étape.</span><span class="sxs-lookup"><span data-stu-id="aee3c-114">Otherwise, skip this step.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aee3c-115">Si vous effectuez cette opération depuis un ordinateur distant, vérifiez que le certificat figure bien sur l'ordinateur exécutant BizTalk Server, et pas seulement sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="aee3c-115">If you are performing this operation from a remote computer, make sure that the certificate exists on the computer running BizTalk Server, and not only on the local computer.</span></span> <span data-ttu-id="aee3c-116">Sinon, l'emplacement de réception ne pourra pas traiter les messages.</span><span class="sxs-lookup"><span data-stu-id="aee3c-116">Otherwise, the receive location will not be able to process messages.</span></span>  
  
5.  <span data-ttu-id="aee3c-117">Si le certificat n’existe pas sur l’ordinateur local, dans le **l’empreinte numérique** zone, tapez ou collez l’empreinte numérique du certificat, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aee3c-117">If the certificate does not exist on the local computer, in the **Thumbprint** box, type or paste the certificate thumbprint, and then click **OK**.</span></span> <span data-ttu-id="aee3c-118">Le format de l'empreinte du certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est un nombre hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="aee3c-118">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee3c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aee3c-119">See Also</span></span>  
 [<span data-ttu-id="aee3c-120">La gestion des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="aee3c-120">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)