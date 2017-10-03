---
title: "Comment attribuer un certificat à un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, assigning
- managing [send ports], certificates
- assigning certificates
- certificates, send ports
ms.assetid: ba9e9c8b-f5b6-4fee-9e89-31b0f1df6ed4
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec19c845c6b0cfb5d19bd7a961fe9ddfbcf2a3d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-a-certificate-to-a-send-port"></a><span data-ttu-id="2e4ce-102">Attribution d'un certificat à un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="2e4ce-102">How to Assign a Certificate to a Send Port</span></span>
<span data-ttu-id="2e4ce-103">Cette rubrique décrit comment attribuer un certificat de sécurité à un port d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-103">This topic describes how to use the BizTalk Server Administration console to assign a security certificate to a send port.</span></span> <span data-ttu-id="2e4ce-104">Le certificat doit figurer dans le magasin de certificats Autres personnes sur l'ordinateur exécutant BizTalk Server, faute de quoi les messages associés à ce port d'envoi ne seront pas traités et des erreurs seront consignées.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-104">The certificate must exist in the Other People certificate store on the computer running BizTalk Server, or messages associated with this send port will not be processed, and errors will be logged.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e4ce-105">Le développeur peut attribuer un certificat de sécurité à un port d'envoi au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-105">The application developer can assign a security certificate to a send port during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2e4ce-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2e4ce-106">Prerequisites</span></span>  
 <span data-ttu-id="2e4ce-107">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="2e4ce-108">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="2e4ce-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-assign-a-certificate-to-a-send-port"></a><span data-ttu-id="2e4ce-109">Pour attribuer un certificat à un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="2e4ce-109">To assign a certificate to a send port</span></span>  
  
1.  <span data-ttu-id="2e4ce-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="2e4ce-111">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi auquel attribuer un certificat.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-111">In the console tree, expand the BizTalk group and the BizTalk application for which you want to assign a certificate to a send port.</span></span>  
  
3.  <span data-ttu-id="2e4ce-112">Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **certificat**.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-112">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Certificate**.</span></span>  
  
4.  <span data-ttu-id="2e4ce-113">Si le certificat existe sur l’ordinateur local, cliquez sur **Parcourir**, accédez au certificat que vous souhaitez attribuer à ce port d’envoi, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-113">If the certificate exists on the local computer, click **Browse**, browse to the certificate that you want to assign to this send port, and then click **OK**.</span></span> <span data-ttu-id="2e4ce-114">Sinon, ignorez cette étape.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-114">Otherwise, skip this step.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e4ce-115">Même si le certificat existe sur l'ordinateur local, il doit également figurer sur l'ordinateur exécutant BizTalk Server (au cas où cet ordinateur serait différent du premier), avant que le port d'envoi puisse traiter les messages.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-115">Even if the certificate exists on the local computer, it must also exist on the computer running BizTalk Server, if different, before the send port will be able to process messages.</span></span>  
  
5.  <span data-ttu-id="2e4ce-116">Si le certificat n’existe pas sur l’ordinateur local, dans le **l’empreinte numérique** zone, tapez ou collez l’empreinte numérique du certificat, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-116">If the certificate does not exist on the local computer, in the **Thumbprint** box, type or paste the certificate thumbprint, and then click **OK**.</span></span> <span data-ttu-id="2e4ce-117">Le format de l'empreinte du certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est un nombre hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="2e4ce-117">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e4ce-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e4ce-118">See Also</span></span>  
 [<span data-ttu-id="2e4ce-119">Création et configuration des Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="2e4ce-119">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)