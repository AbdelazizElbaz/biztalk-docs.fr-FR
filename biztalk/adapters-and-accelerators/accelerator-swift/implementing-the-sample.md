---
title: "Implémentation de l’exemple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd788fd3-b070-40d5-a3d3-ac8e5208cc47
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6622d201c6f7b7d94694a77198d0eb562482489
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="implementing-the-sample"></a>Implémentation de l’exemple
Pour implémenter l’exemple, procédez comme suit :  
  
1.  Créer un nouveau dossier pour SWIFT schémas (\<DocumentSchemaLocation\> dans la syntaxe de l’utilitaire). Tous les schémas pour lesquels vous allez créer/modifier des formulaires InfoPath doivent se trouver dans ce dossier lorsque vous exécutez l’utilitaire.  
  
2.  Si vous générez des formulaires InfoPath pour les messages MT, copiez **SWIFT Base Types.xsd** et **Types.xsd de données courantes SWIFT** de  **\<lecteur :\> \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<Message Pack Version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<Message Pack Version\>\Base schémas** dans le dossier que vous avez créé pour les schémas SWIFT.  
  
3.  Copie tous les schémas pour lesquels vous allez créer des formulaires InfoPath dans le dossier que vous avez créé pour les schémas SWIFT à l’étape 1.  
  
4.  Créez ou désignez un dossier pour conserver le formulaire InfoPath créé les fichiers de solution de modèle (\<DestinationFolderPath\> dans la syntaxe de l’utilitaire). Si vous ne créez pas le dossier de sortie, l’utilitaire créera le même chemin d’accès et le nom que vous passez sur la ligne de commande.  
  
5.  [Facultatif]-Créez un fichier texte \<NameOfFileContainingSchemaList\> qui répertorie les types de messages pour les messages pour lesquels le formulaire InfoPath doit être généré. Par exemple, Type de Message peut être MT103, etc. de MT102. Les noms de Message peuvent être transmis directement via la ligne de commande au lieu de créer ce fichier texte.  
  
## <a name="syntax-of-command-usage-for-formgeneratorexe"></a>Syntaxe d’utilisation de la commande pour FormGenerator.exe  
  
```csharp  
FormGenerator [-b]   [-#] <TemplateFolderPath> [<TemplateFolderPath2>   
   [...<TemplateFolderPath#>]]  
 <DestinationFolderPath>     <DocumentSchemaLocation>  
   { [<SpaceSeparatedDocumentSchemaList>] |   [-f <NameOfFileContainingSchemaList>] }  
  
```  
  
 Où :  
  
-   -b : s’il est spécifié, les formulaires seront compilés après sa création.  
  
-   TemplateFolderPath : le dossier contenant les fichiers de modèle utilisées pour créer la solution InfoPath  
  
-   -#: Si spécifié, les modèles sont recherchées dans plusieurs chemins d’accès de modèle (autant que l’entier numéro # spécifie) et dans l’ordre spécifié.  
  
-   DestinationFolderPath : le dossier où les formulaires doivent être créés  
  
-   DocumentSchemaLocation : emplacement des schémas (y compris les schémas de base et courantes pour les messages du serveur cible maître)  
  
-   SpaceSeparatedDocumentSchemaList : liste séparée par des espaces de schémas comme MT103 MT300.  
  
-   -f: si spécifié, la liste de schéma doit être lue à partir d’un fichier.  
  
-   NameOfFileContainingSchemaList : le nom du fichier contenant la liste.  
  
    > [!NOTE]
    >  La commande ci-dessus est une commande générique pour la catégorie 0, ce dernier et MX messages. Les commandes spécifiques pour générer ces types de formulaires figurent dans le dessous des sections.