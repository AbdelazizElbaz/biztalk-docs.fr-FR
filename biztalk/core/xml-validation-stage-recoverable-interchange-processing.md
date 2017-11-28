---
title: "Étape de Validation XML (traitement des échanges récupérables) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ed00971-d85b-4adb-86c4-c56de7ba7c67
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de8f0225e100053fe6dced8165b7fc800c5e4804
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-validation-stage-recoverable-interchange-processing"></a><span data-ttu-id="d22ca-102">Étape de validation XML (Traitement des échanges récupérables)</span><span class="sxs-lookup"><span data-stu-id="d22ca-102">XML Validation Stage (Recoverable Interchange Processing)</span></span>
<span data-ttu-id="d22ca-103">Le **valideur XML** composant de pipeline traite un échange dans deux modes :</span><span class="sxs-lookup"><span data-stu-id="d22ca-103">The **XML validator** pipeline component processes an interchange in two modes:</span></span>  
  
-   <span data-ttu-id="d22ca-104">**Mode standard**.</span><span class="sxs-lookup"><span data-stu-id="d22ca-104">**Standard mode**.</span></span> <span data-ttu-id="d22ca-105">Lorsque le **valideur XML** composant est configuré pour effectuer une validation standard, les messages contenus dans un échange sont validés dans une unité transactionnelle de travail.</span><span class="sxs-lookup"><span data-stu-id="d22ca-105">When the **XML validator** component is configured to perform standard validation, the messages contained in an interchange are validated in a transactional unit of work.</span></span> <span data-ttu-id="d22ca-106">Plus précisément, si la validation d'un message de l'échange échoue, l'ensemble de l'échange (contenant tous les messages) est placé dans la file d'attente des messages interrompus.</span><span class="sxs-lookup"><span data-stu-id="d22ca-106">Specifically, if validation of a message in the interchange fails, the entire interchange (containing all the messages) is placed in the suspended queue.</span></span>  
  
-   <span data-ttu-id="d22ca-107">**Mode récupérable**.</span><span class="sxs-lookup"><span data-stu-id="d22ca-107">**Recoverable mode**.</span></span> <span data-ttu-id="d22ca-108">Lorsque le **valideur XML** composant est configuré pour effectuer le traitement des échanges récupérables, si la validation d’un message échoue, le message est placé dans la file d’attente suspendue et le **valideur XML** le composant continue à valider les messages restants dans l’échange.</span><span class="sxs-lookup"><span data-stu-id="d22ca-108">When the **XML validator** component is configured to perform recoverable interchange processing, if validation of a message fails, the message is placed in the suspended queue and the **XML validator** component continues to validate remaining messages in the interchange.</span></span>  
  
### <a name="to-configure-recoverable-interchange-processing"></a><span data-ttu-id="d22ca-109">Pour configurer le traitement des échanges récupérables</span><span class="sxs-lookup"><span data-stu-id="d22ca-109">To configure recoverable interchange processing</span></span>  
  
1.  <span data-ttu-id="d22ca-110">Ouvrez un pipeline de réception à l'aide du concepteur de pipeline dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d22ca-110">Open a receive pipeline by using pipeline designer in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="d22ca-111">Faites glisser **valideur XML** composant à partir de la **boîte à outils** à la **Validate** étape du pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="d22ca-111">Drag **XML validator** component from the **Toolbox** to the **Validate** stage of the receive pipeline.</span></span>  
  
3.  <span data-ttu-id="d22ca-112">Dans la fenêtre Propriétés, définissez la valeur de la **traitement des échanges récupérables** propriété **True** si vous souhaitez que le **valideur XML** composant aux échanges de processus mode récupérable, ou affectez à la propriété **False** si vous souhaitez que le composant de traiter les échanges en mode standard.</span><span class="sxs-lookup"><span data-stu-id="d22ca-112">In the Properties window, set the value of the **Recoverable Interchange Processing** property to **True** if you want the **XML validator** component to process interchanges in the recoverable mode, or set the property to **False** if you want the component to process interchanges in the standard mode.</span></span> <span data-ttu-id="d22ca-113">La valeur par défaut de cette propriété est `False`.</span><span class="sxs-lookup"><span data-stu-id="d22ca-113">The default value of this property is `False`.</span></span>  
  
 <span data-ttu-id="d22ca-114">Le **valideur XML** classe dans le modèle objet, qui correspond à la **valideur XML** pipeline composant, a une propriété publique nommée **RecoverableInterchangeProcessing**que vous pouvez utiliser pour obtenir/définir le mode par programme.</span><span class="sxs-lookup"><span data-stu-id="d22ca-114">The **XMLValidator** class in the object model, which corresponds to the **XML validator** pipeline component, has a public property named **RecoverableInterchangeProcessing** that you can use to get/set the mode programmatically.</span></span> <span data-ttu-id="d22ca-115">Consultez la documentation de [Microsoft.BizTalk.Component.XmlValidator](http://msdn.microsoft.com/library/microsoft.biztalk.component.xmlvalidator.aspx) classe pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="d22ca-115">See documentation for [Microsoft.BizTalk.Component.XmlValidator](http://msdn.microsoft.com/library/microsoft.biztalk.component.xmlvalidator.aspx) class for more information.</span></span>  
  
 <span data-ttu-id="d22ca-116">Le tiers d'envoi des messages dont la validation a réussi est identifié en fonction du tiers configuré pour le port de réception sur lequel l'échange parent est arrivé.</span><span class="sxs-lookup"><span data-stu-id="d22ca-116">Messages that are successfully validated have their sending party identified according to the party configured for the receive port on which the parent interchange arrived.</span></span> <span data-ttu-id="d22ca-117">Si la résolution du tiers pour tout message extrait de l'échange échoue, elle est considérée comme ayant échoué pour l'ensemble de l'échange.</span><span class="sxs-lookup"><span data-stu-id="d22ca-117">If party resolution for any message extracted from the interchange fails, then the party resolution is considered to have failed for the entire interchange.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22ca-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d22ca-118">See Also</span></span>  
 [<span data-ttu-id="d22ca-119">Comment configurer le composant de Pipeline valideur XML</span><span class="sxs-lookup"><span data-stu-id="d22ca-119">How to Configure the XML Validator Pipeline Component</span></span>](../core/how-to-configure-the-xml-validator-pipeline-component.md)