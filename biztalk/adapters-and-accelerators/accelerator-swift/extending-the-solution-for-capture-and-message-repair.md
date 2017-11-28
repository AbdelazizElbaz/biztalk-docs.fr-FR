---
title: Extension de la Solution pour la Capture et le Message Repair | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages, errors
- code samples, errors
- errors, code sample
- repairing messages, code sample
- ErrorCollection objects
ms.assetid: 93f463a0-ecff-4f3e-a145-7c506f42c767
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb2f5fb1960a149c96a179ba596c67c9f402016
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-the-solution-for-capture-and-message-repair"></a><span data-ttu-id="a4eb1-102">Extension de la Solution pour la Capture et la réparation de messages</span><span class="sxs-lookup"><span data-stu-id="a4eb1-102">Extending the Solution for Capture and Message Repair</span></span>
<span data-ttu-id="a4eb1-103">Le didacticiel de bout en bout MT103 dans cette aide vous montre comment construire une orchestration BizTalk qui s’abonne aux messages SWIFT ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="a4eb1-103">The MT103 End-to-End Tutorial in this Help shows you how to construct a BizTalk orchestration that subscribes to failed SWIFT messages.</span></span>  
  
 <span data-ttu-id="a4eb1-104">L’orchestration dans le didacticiel de bout en bout MT103 utilise les méthodes statiques d’une classe d’assistance, **ErrorExtractor**, pour extraire la partie de l’erreur et le corps du message sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a4eb1-104">The orchestration in the MT103 End-to-End Tutorial uses the static methods of a helper class, **ErrorExtractor**, to extract the error part and body from the message as strings.</span></span> <span data-ttu-id="a4eb1-105">L’orchestration écrit les parties des fichiers distincts.</span><span class="sxs-lookup"><span data-stu-id="a4eb1-105">The orchestration then writes the parts to separate files.</span></span>  
  
 <span data-ttu-id="a4eb1-106">Étant donné que la partie de l’erreur du message ayant échoué est une sérialisation de la **ErrorCollection** construite par le composant de pipeline, vous pouvez désérialiser la collection et l’utiliser pour automatiser plusieurs de l’erreur de création de rapports et la gestion des.</span><span class="sxs-lookup"><span data-stu-id="a4eb1-106">Because the error part of the failed message is a serialization of the **ErrorCollection** constructed by the pipeline component, you can deserialize the collection and use it to automate more of the error reporting and handling.</span></span> <span data-ttu-id="a4eb1-107">Les éléments suivants [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] fragment de code illustre comment désérialiser la partie de message d’erreur d’un message ayant échoué et itérer sur les erreurs d’analyse dans la collection.</span><span class="sxs-lookup"><span data-stu-id="a4eb1-107">The following [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] code fragment illustrates how to deserialize the error message part of a failed message and iterate over the parsing errors in the collection.</span></span> <span data-ttu-id="a4eb1-108">Le fragment de code omet les qualifications d’espace de noms pour une meilleure lisibilité :</span><span class="sxs-lookup"><span data-stu-id="a4eb1-108">The code fragment omits namespace qualifications for readability:</span></span>  
  
```  
// instantiate an appropriate XmlTextReader  
// xm contains the message  
string sError = ErrorExtractor.GetErrorPartAsString(xm);  
StringReader sRdr = new StringReader(sError);  
XmlTextReader xRdr = new XmlTextReader(sRdr);  
  
// deserialize the collection  
ErrorCollection eC = ErrorCollection.GetErrorCollection(xRdr);  
  
// loop over the parsing errors in the collection  
IEnumerator pEnum = eC.GetParseErrorEnumerator();  
while(pEnum.MoveNext())   
{  
  // pEnum.Current() returns a ParseError object for processing  
}  
  
```  
  
 <span data-ttu-id="a4eb1-109">Le **ErrorCollection** inclut des méthodes pour itérer sur des erreurs par type, ainsi que pour l’itération sur toutes les erreurs dans la collection.</span><span class="sxs-lookup"><span data-stu-id="a4eb1-109">The **ErrorCollection** includes methods for iterating over errors by type as well as for iterating over all of the errors in the collection.</span></span> <span data-ttu-id="a4eb1-110">Pour plus d’informations sur la **ErrorCollection**, consultez ErrorCollection membres.</span><span class="sxs-lookup"><span data-stu-id="a4eb1-110">For more information about the **ErrorCollection**, see ErrorCollection Members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4eb1-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4eb1-111">See Also</span></span>  
 [<span data-ttu-id="a4eb1-112">Messages d’échec et les objets ErrorCollection</span><span class="sxs-lookup"><span data-stu-id="a4eb1-112">Failed Messages and ErrorCollection Objects</span></span>](../../adapters-and-accelerators/accelerator-swift/failed-messages-and-errorcollection-objects.md)