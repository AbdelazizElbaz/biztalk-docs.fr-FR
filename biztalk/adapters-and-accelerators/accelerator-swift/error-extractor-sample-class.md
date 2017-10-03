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
ms.openlocfilehash: 0389f2fdb3f9ccb07bcc8ec9e4cdb1ec510927a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-extractor-sample-class"></a><span data-ttu-id="55abc-102">Exemple d’erreur extracteur, classe</span><span class="sxs-lookup"><span data-stu-id="55abc-102">Error Extractor Sample Class</span></span>
<span data-ttu-id="55abc-103">Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] désassembleur sérialise les erreurs à un objet XML et l’attache l’objet XML à la section de l’erreur d’un message à parties multiples.</span><span class="sxs-lookup"><span data-stu-id="55abc-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] disassembler serializes errors to an XML object, and attaches the XML object to the error section of a multipart message.</span></span> <span data-ttu-id="55abc-104">Le désassembleur publie alors le message ayant échoué sur la base de données MessageBox comme il le ferait un message valide.</span><span class="sxs-lookup"><span data-stu-id="55abc-104">The disassembler then publishes the failed message to the MessageBox database just as it would a valid message.</span></span> <span data-ttu-id="55abc-105">Par conséquent, Échec de détails de l’erreur transporter les messages dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="55abc-105">Therefore, failed messages carry error details into the MessageBox database.</span></span> <span data-ttu-id="55abc-106">Vous pouvez utiliser l’exemple de classe de l’extracteur d’erreur pour extraire les détails de l’erreur à partir d’un message ayant échoué et générer un fichier qui contient les détails de l’erreur et un autre fichier avec le message d’origine.</span><span class="sxs-lookup"><span data-stu-id="55abc-106">You can use the Error Extractor Sample Class to extract the error details from a failed message, and generate one file that has the error details and another file that has the original message.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55abc-107">Erreur extracteur exemple de classe est un exemple de code dans le Kit de développement.</span><span class="sxs-lookup"><span data-stu-id="55abc-107">The Error Extractor Sample Class is sample code in the SDK.</span></span> <span data-ttu-id="55abc-108">Il n’est pas destinée à être utilisé en production.</span><span class="sxs-lookup"><span data-stu-id="55abc-108">It is not intended for use in production.</span></span>  
  
 <span data-ttu-id="55abc-109">Pour utiliser l’exemple de classe de l’extracteur d’erreur, vous devez créer une orchestration pour traiter le message ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="55abc-109">To use the Error Extractor Sample Class, you must create an orchestration to process the failed message.</span></span> <span data-ttu-id="55abc-110">Cette orchestration inclut les étapes pour extraire le corps du message ayant échoué, extraire la partie de l’erreur du message ayant échoué et ensuite écrire le corps et la partie de l’erreur pour séparer les fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="55abc-110">This orchestration includes steps to extract the body of the failed message, extract the error part of the failed message, and then write the body and the error part to separate XML files.</span></span> <span data-ttu-id="55abc-111">L’orchestration représente chacune de ces étapes dans une phase d’expression qui appelle une ou plusieurs des méthodes suivantes dans la classe d’exemple extracteur erreur :</span><span class="sxs-lookup"><span data-stu-id="55abc-111">The orchestration represents each of these steps in an expression stage that calls one or more of the following methods in the Error Extractor Sample Class:</span></span>  
  
## <a name="getbodypartasstring-method"></a><span data-ttu-id="55abc-112">GetBodyPartAsString (méthode)</span><span class="sxs-lookup"><span data-stu-id="55abc-112">GetBodyPartAsString method</span></span>  
 <span data-ttu-id="55abc-113">Cette méthode retourne une chaîne qui contient le code XML se trouve dans le corps du message XLANG 'XML'.</span><span class="sxs-lookup"><span data-stu-id="55abc-113">This method returns a string that contains the XML found in the body part of the XLANG message 'xm'.</span></span> <span data-ttu-id="55abc-114">La méthode attend le message XLANG 'XML' pour contenir un corps appelé « BodySegment ».</span><span class="sxs-lookup"><span data-stu-id="55abc-114">The method expects the XLANG message 'xm' to contain a body part called "BodySegment."</span></span> <span data-ttu-id="55abc-115">Par conséquent, vous devez déclarer 'XML' dans l’orchestration d’appel portant ce nom de partie de corps.</span><span class="sxs-lookup"><span data-stu-id="55abc-115">Therefore, you must declare 'xm' in the calling orchestration with this body part name.</span></span> <span data-ttu-id="55abc-116">Si « BodySegment » n’existe pas dans le cadre de 'XML', **GetBodyPartAsString** lève une exception.</span><span class="sxs-lookup"><span data-stu-id="55abc-116">If "BodySegment" does not exist as a part of 'xm', **GetBodyPartAsString** throws an exception.</span></span>  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetBodyPartAsString(XLANGMessage xm);  
```  
  
## <a name="geterrorpartasstring-method"></a><span data-ttu-id="55abc-117">GetErrorPartAsString (méthode)</span><span class="sxs-lookup"><span data-stu-id="55abc-117">GetErrorPartAsString method</span></span>  
 <span data-ttu-id="55abc-118">Cette méthode retourne une chaîne qui contient le XML trouvé dans la partie de l’erreur du message XLANG 'XML'.</span><span class="sxs-lookup"><span data-stu-id="55abc-118">This method returns a string that contains the XML found in the error part of the XLANG message 'xm'.</span></span> <span data-ttu-id="55abc-119">La méthode attend le message XLANG 'XML' pour contenir une partie de l’erreur appelé « ErrorSegment ».</span><span class="sxs-lookup"><span data-stu-id="55abc-119">The method expects the XLANG message 'xm' to contain an error part called "ErrorSegment."</span></span> <span data-ttu-id="55abc-120">Par conséquent, vous devez déclarer 'XML' dans l’orchestration d’appel portant ce nom de partie d’erreur.</span><span class="sxs-lookup"><span data-stu-id="55abc-120">Therefore, you must declare 'xm' in the calling orchestration with this error part name.</span></span> <span data-ttu-id="55abc-121">Si « ErrorSegment » n’existe pas dans le cadre de 'XML', **GetErrorPartAsString** lève une exception.</span><span class="sxs-lookup"><span data-stu-id="55abc-121">If "ErrorSegment" does not exist as a part of 'xm', **GetErrorPartAsString** throws an exception.</span></span>  
  
```  
SWIFTErrorExtractor.ErrorExtractor.GetErrorPartAsString(XLANGMessage xm);  
```  
  
## <a name="writetofile-method"></a><span data-ttu-id="55abc-122">Méthode WriteToFile</span><span class="sxs-lookup"><span data-stu-id="55abc-122">WriteToFile method</span></span>  
 <span data-ttu-id="55abc-123">Cette méthode écrit la chaîne à partir de la *message* paramètre dans le fichier spécifié par le *filePath* paramètre.</span><span class="sxs-lookup"><span data-stu-id="55abc-123">This method writes the string from the *message* parameter to the file specified by the *filePath* parameter.</span></span>  
  
```  
SWIFTErrorExtractor.ErrorExtractor.WriteToFile(string filePath, string message);  
```  
  
 <span data-ttu-id="55abc-124">Le programme d’installation A4SWIFT installe erreur extracteur exemple de classe (SWIFTErrorExtractor.dll) en tant que partie du Kit de développement A4SWIFT dans \< *lecteur*> : \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tutorial\ SWIFTErrorExtractor.</span><span class="sxs-lookup"><span data-stu-id="55abc-124">A4SWIFT Setup installs the Error Extractor Sample Class (SWIFTErrorExtractor.dll) as part of the A4SWIFT SDK in \<*drive*>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial\SWIFTErrorExtractor.</span></span> <span data-ttu-id="55abc-125">Ce dossier inclut également le code source pour l’exemple de classe (ErrorExtractor.cs).</span><span class="sxs-lookup"><span data-stu-id="55abc-125">This folder also includes the source code for the sample class (ErrorExtractor.cs).</span></span>  
  
 <span data-ttu-id="55abc-126">Pour appeler SWIFTErrorExtractor.dll à partir de l’orchestration, vous devez publier le fichier .dll dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="55abc-126">To call SWIFTErrorExtractor.dll from the orchestration, you must publish the .dll file to the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55abc-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55abc-127">See Also</span></span>  
 [<span data-ttu-id="55abc-128">Outils</span><span class="sxs-lookup"><span data-stu-id="55abc-128">Tools</span></span>](../../adapters-and-accelerators/accelerator-swift/tools.md)