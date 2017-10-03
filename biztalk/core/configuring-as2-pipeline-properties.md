---
title: "Configuration des propriétés de Pipeline AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edir2.AS2.pipeline.properties
ms.assetid: 7faf6b05-710a-4d00-8c77-590ce9d9f962
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e41afd99e7af1441e2d3d8cc936c04cd9321779
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-as2-pipeline-properties"></a><span data-ttu-id="cc341-102">Configuration des propriétés du pipeline AS2</span><span class="sxs-lookup"><span data-stu-id="cc341-102">Configuring AS2 Pipeline Properties</span></span>
<span data-ttu-id="cc341-103">Des propriétés de pipeline sont utilisées dans le traitement d'un message AS2 entrant ou sortant lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas été en mesure de déterminer l'accord correspondant à l'échange envoyé ou reçu.</span><span class="sxs-lookup"><span data-stu-id="cc341-103">Pipeline properties are used in processing an incoming or outgoing AS2 message when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has not been able to determine the agreement that resolves to the sent or received interchange.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cc341-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="cc341-104">Prerequisites</span></span>  
 <span data-ttu-id="cc341-105">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc341-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="as2-pipeline-properties"></a><span data-ttu-id="cc341-106">Propriétés de pipeline AS2</span><span class="sxs-lookup"><span data-stu-id="cc341-106">AS2 Pipeline Properties</span></span>  
 <span data-ttu-id="cc341-107">La propriété suivante peut être définie dans les pipelines AS2 :</span><span class="sxs-lookup"><span data-stu-id="cc341-107">The following property can be set in AS2 pipelines:</span></span>  
  
|<span data-ttu-id="cc341-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="cc341-108">Property</span></span>|<span data-ttu-id="cc341-109">Utiliser</span><span class="sxs-lookup"><span data-stu-id="cc341-109">Use</span></span>|<span data-ttu-id="cc341-110">Valeurs</span><span class="sxs-lookup"><span data-stu-id="cc341-110">Values</span></span>|<span data-ttu-id="cc341-111">Pipeline/Étape</span><span class="sxs-lookup"><span data-stu-id="cc341-111">Pipeline/Stage</span></span>|  
|--------------|---------|------------|---------------------|  
|<span data-ttu-id="cc341-112">ContentTransferEncoding</span><span class="sxs-lookup"><span data-stu-id="cc341-112">ContentTransferEncoding</span></span>|<span data-ttu-id="cc341-113">Indique la méthode à utiliser pour représenter des données binaires au format texte ASCII.</span><span class="sxs-lookup"><span data-stu-id="cc341-113">Indicates which method will be used for representing binary data in ASCII text format.</span></span>|<span data-ttu-id="cc341-114">8 bits (par défaut)</span><span class="sxs-lookup"><span data-stu-id="cc341-114">8bit (default)</span></span><br /><br /> <span data-ttu-id="cc341-115">7 bits</span><span class="sxs-lookup"><span data-stu-id="cc341-115">7bit</span></span><br /><br /> <span data-ttu-id="cc341-116">8 bits</span><span class="sxs-lookup"><span data-stu-id="cc341-116">8bit</span></span>|<span data-ttu-id="cc341-117">AS2EdiSend/Codage</span><span class="sxs-lookup"><span data-stu-id="cc341-117">AS2EdiSend/Encode</span></span><br /><br /> <span data-ttu-id="cc341-118">AS2Send/Codage</span><span class="sxs-lookup"><span data-stu-id="cc341-118">AS2Send/Encode</span></span>|  
  
### <a name="to-set-a-pipeline-property"></a><span data-ttu-id="cc341-119">Pour définir une propriété de pipeline</span><span class="sxs-lookup"><span data-stu-id="cc341-119">To set a pipeline property</span></span>  
  
1.  <span data-ttu-id="cc341-120">Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cliquez avec le bouton droit sur l'emplacement de réception ou sur le port d'envoi qui utilise le pipeline pour lequel définir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="cc341-120">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location or send port using the pipeline that you want to set properties for.</span></span> <span data-ttu-id="cc341-121">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cc341-121">Click **Properties**.</span></span>  
  
2.  <span data-ttu-id="cc341-122">Cliquez sur le bouton représentant des points de suspension (…) en regard du pipeline pour lequel définir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="cc341-122">Click the ellipsis button (…) next to the pipeline that you want to set properties for.</span></span>  
  
3.  <span data-ttu-id="cc341-123">Entrez la valeur de la propriété, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cc341-123">Enter the value for the property, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc341-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc341-124">See Also</span></span>  
 [<span data-ttu-id="cc341-125">Développement et la configuration des Solutions AS2 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cc341-125">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)