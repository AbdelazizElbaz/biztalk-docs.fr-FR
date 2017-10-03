---
title: "Messages représentés en tant que schémas XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Message Assignment shape [Orchestration Designer], maps
- maps, transforms
- Expression Editor, assigning maps
ms.assetid: 646e84d4-1dcc-4f92-9205-84cb6c7df297
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47242dc01ed05ca2ab3c2cb71daffc5a81f9462c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-represented-as-xsd-schemas"></a><span data-ttu-id="b9be2-102">Messages représentés en tant que schémas XSD</span><span class="sxs-lookup"><span data-stu-id="b9be2-102">Messages Represented as XSD Schemas</span></span>
<span data-ttu-id="b9be2-103">Une instance XML de modèle d'un type de message XSD est définie au moment de la conception, puis stockée sur disque.</span><span class="sxs-lookup"><span data-stu-id="b9be2-103">A template XML instance of the XSD message type is defined at design time and then stored on disk.</span></span> <span data-ttu-id="b9be2-104">À l'exécution, un composant .NET récupère le fichier XML sur le disque et le renvoie en tant que valeur XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="b9be2-104">At run time, a .NET component picks up the XML from disk and returns it as an XmlDocument.</span></span> <span data-ttu-id="b9be2-105">Le code d'orchestration peut affecter ce résultat XmlDocument à l'instance de message déclarée dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="b9be2-105">The orchestration code can assign this XmlDocument result to the message instance declared in the orchestration.</span></span>  
  
 <span data-ttu-id="b9be2-106">Le **assignation du Message** forme comporte une seule ligne de code :</span><span class="sxs-lookup"><span data-stu-id="b9be2-106">The **Message Assignment** shape has a single line of code:</span></span>  
  
```  
MsgOut = CreateMsgHelper.Helper.GetXmlDocumentTemplate();  
```  
  
 <span data-ttu-id="b9be2-107">Le composant d'aide qui crée le résultat XmlDocument comporte une méthode statique unique :</span><span class="sxs-lookup"><span data-stu-id="b9be2-107">The Helper Component that creates the XmlDocument has a single static method:</span></span>  
  
```  
private static XmlDocument _template = null;  
private static object _sync = new object();  
private static String LOCATION = @"C:\MyTemplateLocation\MyMsgTemplate.xml";  
  
public static XmlDocument GetXmlDocumentTemplate()  
{  
   XmlDocument doc = _template;  
   if (doc == null)  
   {  
      // Load the doc template from disk.  
      doc = new XmlDocument();  
      XmlTextReader reader = new XmlTextReader(LOCATION);  
      doc.Load(reader);  
  
      // Synchronize assignment to _template.  
      lock (_sync)  
      {  
         XmlDocument doc2 = _template;  
         if (doc2 == null)  
         {  
            _template = doc;  
         }  
         else  
         {  
            // Another thread beat us to it.  
            doc = doc2;  
         }  
      }  
   }  
  
   // Need to explicitly create a clone so that we are not  
   // referencing the same object statically held by this class.  
   doc = (XmlDocument) doc.CloneNode(true);  
   return doc;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9be2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9be2-108">See Also</span></span>  
 <span data-ttu-id="b9be2-109">[Messages représentés en tant que Classes .NET](../core/messages-represented-as-net-classes.md) </span><span class="sxs-lookup"><span data-stu-id="b9be2-109">[Messages Represented as .NET Classes](../core/messages-represented-as-net-classes.md) </span></span>  
 <span data-ttu-id="b9be2-110">[Messages représentés en tant que XLANGMessage](../core/messages-represented-as-xlangmessage.md) </span><span class="sxs-lookup"><span data-stu-id="b9be2-110">[Messages Represented as XLANGMessage](../core/messages-represented-as-xlangmessage.md) </span></span>  
 [<span data-ttu-id="b9be2-111">Construction de Messages dans le Code utilisateur</span><span class="sxs-lookup"><span data-stu-id="b9be2-111">Constructing Messages in User Code</span></span>](../core/constructing-messages-in-user-code.md)