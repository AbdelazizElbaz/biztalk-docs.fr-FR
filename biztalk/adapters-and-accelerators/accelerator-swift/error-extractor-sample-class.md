---
title: Exemple de classe erreur extracteur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Error Extractor Sample class
- errors, Error Extractor Sample class
ms.assetid: d0d59b21-d80a-4466-a77a-1d3b7df1bc2a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53ceb305dcd30164e385022f66140fcaa626b133
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error-extractor-sample-class"></a>Exemple d’erreur extracteur, classe
Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] désassembleur sérialise les erreurs à un objet XML et l’attache l’objet XML à la section de l’erreur d’un message à parties multiples. Le désassembleur publie alors le message ayant échoué sur la base de données MessageBox comme il le ferait un message valide. Par conséquent, Échec de détails de l’erreur transporter les messages dans la base de données MessageBox. Vous pouvez utiliser l’exemple de classe de l’extracteur d’erreur pour extraire les détails de l’erreur à partir d’un message ayant échoué et générer un fichier qui contient les détails de l’erreur et un autre fichier avec le message d’origine.  
  
> [!IMPORTANT]
>  Erreur extracteur exemple de classe est un exemple de code dans le Kit de développement. Il n’est pas destinée à être utilisé en production.  
  
 Pour utiliser l’exemple de classe de l’extracteur d’erreur, vous devez créer une orchestration pour traiter le message ayant échoué. Cette orchestration inclut les étapes pour extraire le corps du message ayant échoué, extraire la partie de l’erreur du message ayant échoué et ensuite écrire le corps et la partie de l’erreur pour séparer les fichiers XML. L’orchestration représente chacune de ces étapes dans une phase d’expression qui appelle une ou plusieurs des méthodes suivantes dans la classe d’exemple extracteur erreur :  
  
## <a name="getbodypartasstring-method"></a>GetBodyPartAsString (méthode)  
 Cette méthode retourne une chaîne qui contient le code XML se trouve dans le corps du message XLANG 'XML'. La méthode attend le message XLANG 'XML' pour contenir un corps appelé « BodySegment ». Par conséquent, vous devez déclarer 'XML' dans l’orchestration d’appel portant ce nom de partie de corps. Si « BodySegment » n’existe pas dans le cadre de 'XML', **GetBodyPartAsString** lève une exception.  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetBodyPartAsString(XLANGMessage xm);  
```  
  
## <a name="geterrorpartasstring-method"></a>GetErrorPartAsString (méthode)  
 Cette méthode retourne une chaîne qui contient le XML trouvé dans la partie de l’erreur du message XLANG 'XML'. La méthode attend le message XLANG 'XML' pour contenir une partie de l’erreur appelé « ErrorSegment ». Par conséquent, vous devez déclarer 'XML' dans l’orchestration d’appel portant ce nom de partie d’erreur. Si « ErrorSegment » n’existe pas dans le cadre de 'XML', **GetErrorPartAsString** lève une exception.  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetErrorPartAsString(XLANGMessage xm);  
```  
  
## <a name="writetofile-method"></a>Méthode WriteToFile  
 Cette méthode écrit la chaîne à partir de la *message* paramètre dans le fichier spécifié par le *filePath* paramètre.  
  
```  
SWIFTErrorExtractor.ErrorExtractor.WriteToFile(string filePath, string message);  
```  
  
 Le programme d’installation A4SWIFT installe erreur extracteur exemple de classe (SWIFTErrorExtractor.dll) en tant que partie du Kit de développement A4SWIFT dans \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tutorial\ SWIFTErrorExtractor. Ce dossier inclut également le code source pour l’exemple de classe (ErrorExtractor.cs).  
  
 Pour appeler SWIFTErrorExtractor.dll à partir de l’orchestration, vous devez publier le fichier .dll dans le global assembly cache.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils](../../adapters-and-accelerators/accelerator-swift/tools.md)