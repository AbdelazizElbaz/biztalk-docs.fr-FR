---
title: "Configuration des propriétés d’accord AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.as2agreement.properties
ms.assetid: a62d8d2a-0b8d-4179-a48f-92f135b5787d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a6f09f85b726869e98712abf354ad3943ce97a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-as2-agreement-properties"></a><span data-ttu-id="6276f-102">Configuration des propriétés de l'accord AS2</span><span class="sxs-lookup"><span data-stu-id="6276f-102">Configuring AS2 Agreement Properties</span></span>
<span data-ttu-id="6276f-103">Cette section décrit les propriétés d'accord sur le transport AS2.</span><span class="sxs-lookup"><span data-stu-id="6276f-103">This section describes AS2 transport agreement properties.</span></span> <span data-ttu-id="6276f-104">Dans les paramètres du protocole de transport, vous pouvez également définir si le message doit être signé, chiffré, etc.</span><span class="sxs-lookup"><span data-stu-id="6276f-104">As part of the transport protocol settings, you can also define whether the message should be signed, whether the message should be encrypted, etc.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6276f-105">La configuration d'un accord AS2 est facultative.</span><span class="sxs-lookup"><span data-stu-id="6276f-105">Configuring an AS2 agreement is optional.</span></span> <span data-ttu-id="6276f-106">Un accord AS2 définit la manière dont les messages sont transférés à l'aide du protocole AS2.</span><span class="sxs-lookup"><span data-stu-id="6276f-106">An AS2 agreement defines how the messages are transferred using the AS2 protocol.</span></span> <span data-ttu-id="6276f-107">Si les partenaires commerciaux décident d'utiliser un autre protocole de transport pour transférer des messages, ils peuvent décider de ne pas définir d'accord AS2.</span><span class="sxs-lookup"><span data-stu-id="6276f-107">If the trading partners decide to use any other transport protocol to transfer messages, they can choose not to define an AS2 agreement.</span></span> <span data-ttu-id="6276f-108">En revanche, les partenaires commerciaux doivent définir un accord sur le codage régissant la manière dont les messages sont formés et codés.</span><span class="sxs-lookup"><span data-stu-id="6276f-108">However, the trading partners must define an encoding agreement that governs how the messages are formed and encoded.</span></span> <span data-ttu-id="6276f-109">Pour plus d’informations sur les contrats de codage, consultez [configuration des propriétés d’encodage de l’accord](../core/configuring-encoding-agreement-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6276f-109">For more information about encoding agreements, see [Configuring Encoding Agreement Properties](../core/configuring-encoding-agreement-properties.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6276f-110">Lorsque vous modifiez un paramètre AS2 dans un accord, vous devez redémarrer l'instance de l'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="6276f-110">Every time you change an AS2 setting in an agreement, you must restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host Instance for the changes to take effect.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6276f-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6276f-111">In This Section</span></span>  
  
-   [<span data-ttu-id="6276f-112">Configuration des paramètres généraux (AS2)</span><span class="sxs-lookup"><span data-stu-id="6276f-112">Configuring General Settings (AS2)</span></span>](../core/configuring-general-settings-as2.md)  
  
-   [<span data-ttu-id="6276f-113">Configuration des identificateurs (AS2)</span><span class="sxs-lookup"><span data-stu-id="6276f-113">Configuring Identifiers (AS2)</span></span>](../core/configuring-identifiers-as2.md)  
  
-   [<span data-ttu-id="6276f-114">Validation de la configuration (AS2)</span><span class="sxs-lookup"><span data-stu-id="6276f-114">Configuring Validation (AS2)</span></span>](../core/configuring-validation-as2.md)  
  
-   [<span data-ttu-id="6276f-115">Configuration des accusés de réception (MDN) (AS2)</span><span class="sxs-lookup"><span data-stu-id="6276f-115">Configuring Acknowledgements (MDNs) (AS2)</span></span>](../core/configuring-acknowledgements-mdns-as2.md)  
  
-   [<span data-ttu-id="6276f-116">Configuration des paramètres de l’hôte Local (AS2)</span><span class="sxs-lookup"><span data-stu-id="6276f-116">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)  
  
-   [<span data-ttu-id="6276f-117">Configuration des certificats de Signature (AS2)</span><span class="sxs-lookup"><span data-stu-id="6276f-117">Configuring Signature Certificates (AS2)</span></span>](../core/configuring-signature-certificates-as2.md)  
  
-   [<span data-ttu-id="6276f-118">Configuration de l’Association de Port d’envoi (AS2)</span><span class="sxs-lookup"><span data-stu-id="6276f-118">Configuring Send Port Association (AS2)</span></span>](../core/configuring-send-port-association-as2.md)  
  
## <a name="see-also"></a><span data-ttu-id="6276f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6276f-119">See Also</span></span>  
 [<span data-ttu-id="6276f-120">Configuration des propriétés AS2</span><span class="sxs-lookup"><span data-stu-id="6276f-120">Configuring AS2 Properties</span></span>](../core/configuring-as2-properties.md)