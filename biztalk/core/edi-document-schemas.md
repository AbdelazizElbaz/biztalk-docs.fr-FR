---
title: "Schémas de Document EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc3a30b8-0686-4c06-985b-13f2c95f8e99
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b96089f7f76af1183f457202bb2e22b5be7f146
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="edi-document-schemas"></a>Schémas de document EDI
Les schémas de document définissent le corps d'un type de document de transaction EDI.  
  
## <a name="schema-delivery-and-setup"></a>Réception et configuration du schéma  
 Schémas de document EDI sont remis dans un état compressé dans un fichier exécutable à extraction automatique, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\MicrosoftEdiXSDTemplates.exe. Le fichier exécutable à extraction automatique garantit qu’une structure de dossiers appropriée est créé (par le type de codage et les sous-types version/publication). Une fois exécuté, il dépose les schémas EANCOM, EDIFACT, HIPAA et X12 dans des sous-dossiers au sein du répertoire de l'exécutable.  
  
 Les espaces de noms de schémas par défaut sont :  
  
-   Pour X12 : `http://schemas.microsoft.com/BizTalk/EDI/X12/2006`  
  
-   Pour EDIFACT : `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006`  
  
## <a name="schema-naming-convention"></a>Convention d'affectation de noms de schémas  
 La convention d’affectation de noms pour le X12 et type de codage EDIFACT est \<codage\>_\<Version\>\<version\>\_\<Doctype\>. En voici quelques exemples : le schéma X12_00401_864.xsd pour le type de document X12 864 (version d'origine 004, version finale 01) et le schéma EDIFACT_D01C_AUTHOR.xsd pour le type de document EDIFACT AUTHOR (version d'origine D01, version finale C).  
  
> [!NOTE]
>  Le nom d'un schéma EDIFACT est sensible à la casse. Par exemple, EFACT_D98B_ORDERS et EFACT_d98B_Orders désignent deux schémas différents.  
  
## <a name="schema-contents"></a>Contenu des schémas  
 Un schéma de document X12 démarre avec un en-tête de document informatisé ST et se termine avec un code de fin de document informatisé SE. Un schéma de document EDIFACT démarre avec un en-tête de message UNH et un code de fin de message UNT. Le schéma définit chaque élément de données de ces en-têtes et codes de fin.  
  
 Un schéma de document définit ensuite chaque segment du document informatisé ou du message, ainsi que les éléments de données au sein de ces segments. Par exemple, le schéma X12_00401_864.xsd définit les éléments BMG01, BMG02 et BMG03 des segments BMG. Le schéma spécifie les caractéristiques du type de données complexes du segment, telles que l'ordre des champs, le type de délimiteur et l'espace de noms. Si le segment contient des règles de validation de champs croisés, le schéma définit celles-ci. Pour plus d’informations, consultez [Validation croisée du Segment de champ](../core/cross-field-segment-validation.md).  
  
 Le schéma spécifie les caractéristiques de chaque élément de données du segment, telles que le type de données simples, le nombre minimal d'occurrences, la longueur minimale et la longueur maximale.  
  
 Si le type de message contient une boucle, le schéma définit les éléments de données de chaque boucle, le nombre minimal et maximal d'occurrences de la boucle, et si la boucle est liée ou non. Il définit également l'imbrication d'un segment, et si la boucle est explicite ou implicite.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure des messages EDI](../core/edi-message-structure.md)   
 [Validation des messages EDI](../core/edi-message-validation.md)