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
# <a name="messages-represented-as-xsd-schemas"></a>Messages représentés en tant que schémas XSD
Une instance XML de modèle d'un type de message XSD est définie au moment de la conception, puis stockée sur disque. À l'exécution, un composant .NET récupère le fichier XML sur le disque et le renvoie en tant que valeur XmlDocument. Le code d'orchestration peut affecter ce résultat XmlDocument à l'instance de message déclarée dans l'orchestration.  
  
 Le **assignation du Message** forme comporte une seule ligne de code :  
  
```  
MsgOut = CreateMsgHelper.Helper.GetXmlDocumentTemplate();  
```  
  
 Le composant d'aide qui crée le résultat XmlDocument comporte une méthode statique unique :  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Messages représentés en tant que Classes .NET](../core/messages-represented-as-net-classes.md)   
 [Messages représentés en tant que XLANGMessage](../core/messages-represented-as-xlangmessage.md)   
 [Construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md)