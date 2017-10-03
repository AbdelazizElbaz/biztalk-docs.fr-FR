---
title: "Délimiteur préservation et Suppression de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30985b94-625e-411a-8137-1c129bc197bf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1195e153eb94215bf8861b4856e4d2135b24443e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="delimiter-preservation-and-suppression"></a>Suppression et la préservation de délimiteur

## <a name="overview"></a>Vue d'ensemble
Il existe deux propriétés qui s’appliquent aux enregistrements délimités : **préserver le délimiteur pour les données vides** et **[Supprimer les délimiteurs de**. Ces propriétés permettent de contrôler la façon dont l’assembleur de fichier plat gère les délimiteurs associés aux données inexistantes et des délimiteurs de fin. Lorsque vous définissez la **préserver le délimiteur pour les données vides** propriété **Oui** (qui est le paramètre par défaut), les délimiteurs sont inclus dans le message de fichier plat converti pour :  
  
-   les champs sans données ;  
  
-   les enregistrements immédiatement subordonnés sans donnée associés à aucune balise.  
  
 Lorsque vous définissez la **préserver le délimiteur pour les données vides** propriété **non**, délimiteurs ne sont pas inclus dans le fichier plat converti pour les enregistrements et champs sans données. Quel que soit le paramètre de la **préserver le délimiteur pour les données vides** propriété délimiteurs de ne pas être inclus dans le message de fichier plat converti pour les enregistrements immédiatement subordonnés sans données pour lequel une balise est définie.  
  
 Lorsque vous définissez la **supprimer les délimiteurs** propriété **non** (qui est le paramètre par défaut), un ou plusieurs des délimiteurs de fin peuvent être inclus dans le message de fichier plat converti. Lorsque vous définissez la **supprimer les délimiteurs** propriété **Oui**, les délimiteurs ne sont pas inclus dans le message de fichier plat converti.  

## <a name="special-scenarios"></a>Scénarios spécifiques  
 Il existe certains cas, les comportements induits par les paramètres de la **préserver le délimiteur pour les données vides** et **supprimer les délimiteurs** propriétés peuvent être en conflit. Dans ce cas, les comportements associés à la dernière propriété, **supprimer les délimiteurs**, est prioritaire. Dans certains cas encore, un message vous préviendra de conflits potentiels entre les paramètres que vous avez choisis pour ces deux propriétés.  
  
 Par exemple, considérez un **enregistrement** nœud défini avec les valeurs de propriété suivantes :  
  
-   Le nom du nœud est MyRec  
  
-   L’identificateur de balise est Rec  
  
-   Le délimiteur enfant est ,  
  
-   Le classement enfant est Infix  
  
 Et défini pour contenir cinq **Fieldelement** nœuds avec les noms suivants (elles peuvent également être **attribut de champ** nœuds ou subordonné **enregistrement** nœuds) :  
  
-   FieldElem1  
  
-   FieldElem2  
  
-   FieldElem3  
  
-   FieldElem4  
  
-   FieldElem5  
  
 Ensuite, supposons que les éléments suivants fragment XML pratiquement vide, représentant ce **enregistrement** nœud, est passé à l’assembleur de fichier plat.  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <FieldElem4 />  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 Le tableau suivant montre la sortie produite et la propriété associée supplémentaire, configuration requise pour les nœuds de schéma approprié, en fonction des paramètres différents pour le **préserver le délimiteur pour les données vides** (PDFED) et **Supprimer les délimiteurs de** les propriétés (STD).  
  
|Paramètre PDFED|Paramètre STD|Sortie|Autres conditions requises pour le nœud|  
|---|---|---|---|  
|Oui|Non|Rec,,,Val,,|Aucun.|  
|Non|Oui|Rec,Val|Tous les **élément de champ** nœuds doivent être configurés comme facultatifs.|  
|Oui|Oui|Rec,,,Val|Nœuds nommés **FieldElem4** et **FieldElem5** doivent être configurés comme facultatifs.|  
|Non|Non|Rec,Val,,|Tous les **élément de champ** nœuds doivent être configurés comme facultatifs.|  
  
 Lorsque ces paramètres de propriété spécifient que les délimiteurs ne doivent pas être préservés ou doivent être supprimés, un message vous avertissant que l'analyse des données du fichier plat sérialisées à l'aide du même schéma risque d'être impossible est envoyé dans les deux cas suivants :  
  
-   Lorsque le **enregistrement** nœud pour lequel la **préserver le délimiteur pour les données vides** est définie sur **non** et/ou la **supprimer les délimiteurs de**est définie sur **Oui**, respectivement, contient subordonnés **Fieldelement** nœuds, **attribut de champ** nœuds, ou **enregistrement**  nœuds pour lesquels aucune balise n’est spécifié.  
  
-   Lorsque le subordonné **élément de champ** nœuds, **attribut de champ** nœuds, et **enregistrement** nœuds pour lesquels aucune balise n’est spécifiée ne sont pas configurés pour être facultatif (en définissant le **Min Occurs** propriété définie à zéro) dans le schéma. Lorsque le **supprimer les délimiteurs** est définie sur **Oui**, seule la dernière nœuds subordonnés doivent être configurés comme facultatifs. Lorsque le **préserver le délimiteur pour les données vides** est définie sur **non**, tous les nœuds subordonnés doivent être configurés comme facultatifs.  
  
> [!NOTE]
>  Délimiteurs sont toujours conservés lorsque l’élément XML associé à un (la vraisemblablement facultatif) **enregistrement**, **Fieldelement**, ou **attribut de champ** nœud est entièrement absent à partir de la représentation XML du document commercial, sauf lorsqu’un enregistrement suit un champ facultatif manquant. En d'autres termes, lorsque les données ainsi que les balises XML les entourant sont absentes, le délimiteur correspondant est toujours inclus dans la représentation de fichier plat du document commercial.  
  
 Modifiez à présent le schéma de sorte qu'il inclue un enregistrement enfant et deux éléments champ qui viennent à la suite d'un champ élément manquant. Les éléments d’enregistrement enfant sont configurés pour utiliser le &#124; (verticale) comme délimiteur.  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <!-- <FieldElem4 /> -->  
    <ChildRec>  
        <InnerFieldElement1>Inner1</InnerFieldElement1>   
        <InnerFieldElement2>Inner2</InnerFieldElement1>  
    </ChildRec>  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 Si ceci est passé au désassembleur de fichier plat, les délimiteurs de FieldElem4  ne seront pas préservés mais les enregistrements suivants seront délimités comme prévu.  
  
```  
,,Val,,Inner1,Inner2,,  
```  
  
## <a name="see-also"></a>Voir aussi  
-  [Considérations concernant les enregistrements délimités](../core/delimited-record-considerations.md)   
-  **Préserver le délimiteur pour les données vides (propriété de nœud des schémas de fichier plat)** et **supprimer les délimiteurs (propriété de nœud des schémas de fichier plat) de fin**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]