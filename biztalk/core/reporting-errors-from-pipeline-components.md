---
title: "Rapports d’erreurs à partir des composants de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IErrorInfo object
- pipeline components [custom], errors
- SetErrorInfo method
- Exception object
ms.assetid: ad7c519e-829a-4a92-a42f-3e367d5dbaa8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c111a0c10f4316e7b29e873adf53a8e6b9a9acd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="reporting-errors-from-pipeline-components"></a><span data-ttu-id="d92f2-102">Rapports d’erreurs à partir des composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="d92f2-102">Reporting Errors from Pipeline Components</span></span>
<span data-ttu-id="d92f2-103">Les composants de pipeline signalent les erreurs de deux manières :</span><span class="sxs-lookup"><span data-stu-id="d92f2-103">Pipeline components report errors in two ways:</span></span>  
  
-   <span data-ttu-id="d92f2-104">Pour les composants .NET, en levant une exception.</span><span class="sxs-lookup"><span data-stu-id="d92f2-104">For .NET-based components, by throwing an exception.</span></span>  
  
-   <span data-ttu-id="d92f2-105">Pour les composants COM, en définissant le **ErrorInfo** objet et en retournant un HRESULT d’échec.</span><span class="sxs-lookup"><span data-stu-id="d92f2-105">For COM-based components, by setting the **ErrorInfo** object and returning a failure HRESULT.</span></span>  
  
## <a name="reporting-errors-from-net-pipeline-components"></a><span data-ttu-id="d92f2-106">Signalement des erreurs par les composants de pipeline .NET</span><span class="sxs-lookup"><span data-stu-id="d92f2-106">Reporting errors from .NET pipeline components</span></span>  
 <span data-ttu-id="d92f2-107">Pour signaler une erreur, un composant de pipeline .NET doit lever une exception à l'emplacement où il signale la description de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="d92f2-107">To report an error, a .NET-based pipeline component needs to throw an exception where it reports the error description.</span></span> <span data-ttu-id="d92f2-108">Pour signaler le nom du composant qui génère une erreur, définissez la **Source** propriété de la **Exception** objet.</span><span class="sxs-lookup"><span data-stu-id="d92f2-108">To report the name of the component that throws an error, set the **Source** property of the **Exception** object.</span></span>  
  
 <span data-ttu-id="d92f2-109">Le moteur de messagerie utilise le **Message** et **Source** propriétés de la **Exception** objet pour signaler une erreur.</span><span class="sxs-lookup"><span data-stu-id="d92f2-109">The Messaging Engine uses the **Message** and **Source** properties of the **Exception** object to report an error.</span></span> <span data-ttu-id="d92f2-110">Le message suivant est écrit dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="d92f2-110">The following message is written to the event log:</span></span>  
  
 <span data-ttu-id="d92f2-111">« Échec de l’exécution de la [de réception &#124; envoi] pipeline : \<nom du pipeline\> Source : \<Source\> [emplacement de réception &#124; Port d’envoi :] \<emplacement &#124; nom de port\> raison : \<Message\>. »</span><span class="sxs-lookup"><span data-stu-id="d92f2-111">"There was a failure executing the [receive&#124;send] pipeline: \<pipeline name\> Source: \<Source\> [Receive Location&#124;Send Port:] \<location&#124;port name\> Reason: \<Message\>."</span></span>  
  
## <a name="reporting-errors-from-com-pipeline-components"></a><span data-ttu-id="d92f2-112">Signalement d'erreurs par les composants de pipeline COM</span><span class="sxs-lookup"><span data-stu-id="d92f2-112">Reporting errors from COM pipeline components</span></span>  
 <span data-ttu-id="d92f2-113">Pou signaler une erreur, les composants de pipeline COM effectuent les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d92f2-113">To report an error, COM-based pipeline components perform the following actions:</span></span>  
  
1.  <span data-ttu-id="d92f2-114">Le composant de pipeline définit la **IErrorInfo** objet en appelant le **SetErrorInfo** (méthode).</span><span class="sxs-lookup"><span data-stu-id="d92f2-114">The pipeline component sets the **IErrorInfo** object by calling the **SetErrorInfo** method.</span></span>  
  
2.  <span data-ttu-id="d92f2-115">Il retourne une valeur HRESULT d'échec au moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="d92f2-115">The pipeline component returns a failed HRESULT to the Messaging Engine.</span></span>  
  
 <span data-ttu-id="d92f2-116">Le moteur de messagerie utilise le **GetSource** et **GetDescription** propriétés de la **IErrorInfo** objet pour signaler une erreur.</span><span class="sxs-lookup"><span data-stu-id="d92f2-116">The Messaging Engine uses the **GetSource** and **GetDescription** properties of the **IErrorInfo** object to report an error.</span></span> <span data-ttu-id="d92f2-117">Si la source n'est pas définie, le nom du composant est utilisé.</span><span class="sxs-lookup"><span data-stu-id="d92f2-117">If the source is not set, the name of the component is used.</span></span> <span data-ttu-id="d92f2-118">Si la description n’est pas définie ou la totalité de **ErrorInfo** objet n’est pas défini, le HRESULT retourné est signalé au lieu de la description.</span><span class="sxs-lookup"><span data-stu-id="d92f2-118">If the description is not set or the whole **ErrorInfo** object is not set, the returned HRESULT is reported instead of the description.</span></span> <span data-ttu-id="d92f2-119">Le message suivant est écrit dans le journal des événements :</span><span class="sxs-lookup"><span data-stu-id="d92f2-119">The following message is written to the event log:</span></span>  
  
 <span data-ttu-id="d92f2-120">« Échec de l’exécution de la [de réception &#124; envoi] pipeline : \<nom du pipeline\> Source : \<GetSource\> [emplacement de réception &#124; Port d’envoi :] \<emplacement &#124; nom de port\> raison : \<GetDescription ou HRESULT\>. »</span><span class="sxs-lookup"><span data-stu-id="d92f2-120">"There was a failure executing the [receive&#124;send] pipeline: \<pipeline name\> Source: \<GetSource\> [Receive Location&#124;Send Port:] \<location&#124;port name\> Reason: \<GetDescription or HRESULT\>."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d92f2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d92f2-121">See Also</span></span>  
 [<span data-ttu-id="d92f2-122">Développement des composants de pipeline personnalisés</span><span class="sxs-lookup"><span data-stu-id="d92f2-122">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)