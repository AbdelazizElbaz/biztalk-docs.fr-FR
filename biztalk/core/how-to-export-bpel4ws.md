---
title: Comment exporter BPEL4WS | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BPEL4WS, exporting
- BPEL4WS, restrictions
- orchestrations, BPEL4WS
ms.assetid: 4648dfcf-cf48-4471-b088-07252c080fb8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b16c2e34b498a9fb8d5fd3f6e69f022c2876a763
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bpel4ws"></a>Comment exporter BPEL4WS
Vous pouvez exporter une orchestration BizTalk existante vers BPEL4WS.  
  
> [!IMPORTANT]
>  Cette version de BizTalk Server est compatible avec BPEL4WS 1.1. Vous ne pouvez pas importer ni exporter BPEL4WS 1.0.  
  
 Si vous effectuez une exportation, la compatibilité de BPEL4WS pour la compilation exige que les orchestrations ne contiennent que des composants communs à XLANG/s et à BPEL4WS, ou des composants pouvant être convertis en BPEL4WS sans que leur comportement n'en soit modifié.  
  
## <a name="export-restrictions-on-orchestrations-for-bpel4ws-compliance"></a>Limites d’exportation imposées aux orchestrations pour des raisons de compatibilité avec BPEL4WS  
  
-   Vous ne pouvez pas utiliser la forme Appeler orchestration ou la forme Démarrer orchestration.  
  
-   Vous ne pouvez pas utiliser la forme Transformer.  
  
-   Vous ne pouvez pas appeler de méthodes sur les composants .NET personnalisés.  
  
-   Vous ne pouvez pas appliquer un délai à une transaction à long terme.  
  
-   Votre orchestration ne peut pas accepter de paramètres.  
  
-   Les gestionnaires de compensation pouvant être appelés ne peuvent pas avoir de paramètres.  
  
-   Les types de variables doivent être pris en charge dans XPATH.  
  
-   Vous ne pouvez pas utiliser la forme Interrompre.  
  
-   Les valeurs littérales doivent être un des types suivants :  
  
     boolean, char, byte, sbyte, int32, uint32, int64, uint64, single, double, string  
  
-   Les opérateurs arithmétiques ne sont autorisés que sur les opérandes de types numériques suivants :  
  
     byte, sbyte, int32, uint32, int64, uint64, single, double  
  
-   Les opérateurs relationnels ne peuvent pas être appliqués au type char.  
  
-   Vous ne pouvez pas faire référence à une propriété de liaison de service dans une expression.  
  
-   Vous ne pouvez pas effectuer d’actions entre un **envoyer** forme et un **réception** forme qui utilisent le même port requête-réponse sortant.  
  
-   Vous ne pouvez pas faire référence à un service Web de façon indirecte, comme à travers une référence à un autre projet contenant une référence. Vous devez explicitement référencer le service Web dans votre projet.  
  
-   Vous ne pouvez pas indiquer de valeur DateTime ou TimeSpan constante dans un délai. Utilisez à la place une des classes de conversion dans l'espace de noms System.Xml :  
  
     Pour une valeur DateTime constante : System.Xml.XmlConvert.ToDateTime, par exemple System.Xml.XmlConvert.ToDateTime("2004-04-15")  
  
     Pour une valeur TimeSpan constante : System.Xml.XmlConvert.ToTimeSpan, par exemple System.Xml.XmlConvert.ToTimeSpan("2004-04-15")  
  
> [!NOTE]
>  Les caractères littéraux sont exportés sous forme d'entiers non signés. Par exemple, « a » est exporté en tant que 97, « b » en tant que 98 et ainsi de suite.  
  
> [!CAUTION]
>  Les noms d'identificateur doivent respecter la spécification W3C Extensible Markup Language (XML) 1.0.  
  
#### <a name="to-export-an-orchestration-to-bpel4ws"></a>Pour exporter une orchestration vers BPEL4WS  
  
1.  Ajoutez un nouvel élément de type Orchestration BizTalk à votre projet.  
  
2.  Cliquez sur la surface de conception pour afficher la fenêtre Propriétés d'orchestration.  
  
3.  Définissez **Module Exportable** sur True.  
  
4.  Type dans l’espace de noms pour **Module XML cible Namespace**.  
  
5.  Définissez **Orchestration Exportable** sur True.  
  
6.  Type dans l’espace de noms pour **Orchestration XML cible Namespace**.  
  
7.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le fichier .ODX de votre orchestration.  
  
8.  Sélectionnez **exporter vers BPEL**.  
  
     Votre orchestration sera exportée vers BPEL4WS. Consultez la fenêtre Sortie et la liste des tâches pour confirmer le succès de l’opération ou diagnostiquer des problèmes. Une fois que votre exportation a réussi, un fichier .WSDL et un fichier .BPEL seront créés dans le répertoire de votre projet.  
  
> [!NOTE]
>  Si votre orchestration contient une assignation à un lien de rôle (lien de service) ou une assignation littérale à un port dynamique, BizTalk génère une référence à un point de terminaison BPEL4WS factice et émet un avertissement.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment importer BPEL4WS](../core/how-to-import-bpel4ws.md)   
 [XLANG-s pour les Conversions de Type BPEL4WS](../core/xlang-s-to-bpel4ws-type-conversions.md)