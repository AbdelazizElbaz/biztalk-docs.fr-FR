---
title: "Comment configurer le composant de Pipeline résolution du tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authenticating, Partner Management
- Party Resolution [pipeline component], configuring
- Partner Management, authenticating
- pipeline components, Party Resolution
ms.assetid: 0ebd30f7-3a6b-4457-8e30-80bf81fbd28d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0c78792cd7c61ed1297954625fbd7da5aedfa04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-party-resolution-pipeline-component"></a><span data-ttu-id="e0085-102">Configuration du composant de pipeline Résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="e0085-102">How to Configure the Party Resolution Pipeline Component</span></span>
<span data-ttu-id="e0085-103">Le composant de pipeline Résolution du tiers permet de mapper l'ID de sécurité de l’utilisateur et l'objet du certificat du client vers un tiers BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e0085-103">The Party Resolution pipeline component is used to map the user security ID and the certificate subject for the client to a BizTalk Server party.</span></span> <span data-ttu-id="e0085-104">Le mappage est utilisé pour appliquer l’authentification des tiers envoyant des messages à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e0085-104">The mapping is used to enforce authentication of the parties who send messages to BizTalk Server.</span></span> <span data-ttu-id="e0085-105">Pour plus d’informations sur la gestion des partenaires, consultez[la création d’un accord](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).</span><span class="sxs-lookup"><span data-stu-id="e0085-105">For more information about partner management, see[How to Create an Agreement](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0085-106">Pour permettre au composant de pipeline Résolution du tiers de valider un utilisateur Windows, vous devez ajouter l’alias WindowsUser à un tiers.</span><span class="sxs-lookup"><span data-stu-id="e0085-106">To enable the Party Resolution pipeline component to validate a Windows user, you must add the WindowsUser alias to a party.</span></span> <span data-ttu-id="e0085-107">Pour plus d’informations, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="e0085-107">For more information, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span>  
  
### <a name="to-configure-the-properties-for-the-party-resolution-pipeline-component"></a><span data-ttu-id="e0085-108">Pour configurer les propriétés du composant de pipeline Résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="e0085-108">To configure the properties for the Party Resolution pipeline component</span></span>  
  
1.  <span data-ttu-id="e0085-109">Faites glisser le composant de pipeline Résolution du tiers dans la phase de résolution de tiers d'un pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="e0085-109">Drag the Party Resolution pipeline component into the ResolveParty stage of a receive pipeline.</span></span>  
  
2.  <span data-ttu-id="e0085-110">Dans la fenêtre Propriétés, dans le **propriétés du composant de Pipeline** section, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="e0085-110">In the Properties window, in the **Pipeline Component Properties** section, do the following.</span></span>  
  
    |<span data-ttu-id="e0085-111">Utiliser</span><span class="sxs-lookup"><span data-stu-id="e0085-111">Use this</span></span>|<span data-ttu-id="e0085-112">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="e0085-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e0085-113">**Résoudre le tiers par le certificat**</span><span class="sxs-lookup"><span data-stu-id="e0085-113">**Resolve Party By Certificate**</span></span>|<span data-ttu-id="e0085-114">La valeur **True** si vous souhaitez activer la résolution de tiers en fonction de l’empreinte numérique du certificat de signature du tiers à partir duquel les messages sont reçus.</span><span class="sxs-lookup"><span data-stu-id="e0085-114">Set to **True** if you want to enable party resolution based on the thumbprint of the signature certificate from the party from where the messages are received.</span></span><br /><br /> <span data-ttu-id="e0085-115">Valeur par défaut : **True**</span><span class="sxs-lookup"><span data-stu-id="e0085-115">Default value: **True**</span></span>|  
    |<span data-ttu-id="e0085-116">**Résoudre le tiers par le SID**</span><span class="sxs-lookup"><span data-stu-id="e0085-116">**Resolve Party By SID**</span></span>|<span data-ttu-id="e0085-117">La valeur **True** si vous souhaitez activer la résolution de tiers en fonction de l’identificateur de sécurité (SID) du compte de l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="e0085-117">Set to **True** if you want to enable party resolution based on the security identifier (SID) of the sender account.</span></span><br /><br /> <span data-ttu-id="e0085-118">Si les deux propriétés sont définies sur **True**, le **résoudre le tiers par certificat** propriété est prioritaire sur la **résoudre le tiers par SID** propriété, ce qui signifie que si les deux le certificat et l’identificateur de sécurité sont disponibles, le sujet du certificat est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e0085-118">If both properties are set to **True**, the **Resolve Party By Certificate** property takes precedence over the **Resolve Party By SID** property, meaning that if both the certificate and the SID are available, the certificate subject is used.</span></span> <span data-ttu-id="e0085-119">Si le tiers ne peut pas être résolu à l’aide de l’objet du certificat, le composant ne tombe pas dans le **résoudre le tiers par SID** propriété et la valeur par défaut (s-1-5-7) est appliquée pour **BTS. SourcePartyID**.</span><span class="sxs-lookup"><span data-stu-id="e0085-119">If the party cannot be resolved by using the certificate subject, the component does not fall back to the **Resolve Party By SID** property, and the default value (s-1-5-7) is stamped for **BTS.SourcePartyID**.</span></span><br /><br /> <span data-ttu-id="e0085-120">Valeur par défaut : **True**</span><span class="sxs-lookup"><span data-stu-id="e0085-120">Default value: **True**</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e0085-121">Si vous utilisez l’adaptateur BizTalk Message Queuing et vous souhaitez résoudre le tiers en fonction de nom d’utilisateur, définissez **résoudre le tiers par certificat** à **False** et **résoudre le tiers par SID** à **True**.</span><span class="sxs-lookup"><span data-stu-id="e0085-121">If you use the BizTalk Message Queuing adapter and want to resolve the party based on user name, set **Resolve Party By Certificate** to **False** and **Resolve Party By SID** to **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0085-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0085-122">See Also</span></span>  
 <span data-ttu-id="e0085-123">[Composant de Pipeline résolution du tiers](../core/party-resolution-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="e0085-123">[Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md) </span></span>  
 <span data-ttu-id="e0085-124">[Configuration des composants de Pipeline natifs](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="e0085-124">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 [<span data-ttu-id="e0085-125">Résolution du tiers personnalisé (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="e0085-125">Custom Party Resolution (BizTalk Server Sample)</span></span>](../core/custom-party-resolution-biztalk-server-sample.md)