---
title: "Procédure : utiliser des Types de ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, port types
- port types, deleting
- port types, Web
- port types, request-response
- orchestrations, ports
- port types, modifier
- port types
- ports, port types
- port types, one-way
ms.assetid: 78ac731e-c330-4888-a9ee-10523fef8ed0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e3b4307cb9d48679ae1b90f7e02dd0288ec2957
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-work-with-port-types"></a>L’utilisation des Types de ports
Un type de port est composé d'un modèle de communication, d'un ensemble d'opérations (requêtes ou réponses) et des types de messages dont ces opérations peuvent s'occuper. Le modèle peut être de type unidirectionnel ou requête-réponse (bidirectionnel) et toutes les opérations définies sur ce type de port doivent utiliser le même modèle. Notez que les types de ports sont indépendants de la direction : direction est spécifiée sur chaque port.  
  
 L’étendue d’un type de port est définie par le **modificateur de Type** propriété. Le type de port peut être public, privé ou interne. S'il est public, il est visible par toute personne interagissant avec l'orchestration. S'il est privé, il est visible par les autres orchestrations appartenant aux mêmes projet et nom d'espaces. S'il est interne, il n'est visible que dans le projet. Dans la mesure où une définition de type de port inclut des types de messages, l'étendue du type de message doit englober celle de tout type de port l'utilisant.  
  
> [!NOTE]
>  Un type de port peut être appliqué à n'importe quel nombre de ports. Un port peut être considéré comme une instance d'un type de port.  
  
> [!NOTE]
>  Un type de port ne comporte pas par essence une direction de communication ; la direction se définit sur chaque port.  
  
### <a name="to-add-a-request-response-port-type"></a>Pour ajouter un type de port de requête-réponse  
  
1.  Dans la fenêtre Vue Orchestration, cliquez sur **Types de ports** puis cliquez sur **Type de Port de requête-réponse nouveau**.  
  
     Le **Types de ports** nœud se développe, s’il était réduit et un nouveau type de port requête-réponse est ajouté avec une opération par défaut.  
  
2.  Indiquez un nom pour le type de port.  
  
3.  Définissez une ou plusieurs opérations de port.  
  
     Vous pouvez nommer vos opérations de port, mais si vous les sélectionnez à partir d'un autre projet, ils seront affichés uniquement en tant que « Requête » et « Réponse ». Si vous sélectionnez une opération de port à partir d'un autre projet, vérifiez qu'elle possède le type de message correct.  
  
### <a name="to-add-a-one-way-port-type"></a>Pour ajouter un type de port unidirectionnel  
  
1.  Dans la fenêtre Vue Orchestration, cliquez sur **Types de ports** puis cliquez sur **nouveau Type de Port unidirectionnel**.  
  
     Le **Types de ports** nœud se développe, s’il était réduit et un nouveau type de port unidirectionnel est ajouté avec une opération par défaut.  
  
2.  Indiquez un nom pour le type de port.  
  
3.  Définissez une ou plusieurs opérations de port.  
  
### <a name="to-add-a-web-port-type"></a>Pour ajouter un type de port Web  
  
-   Ajoutez une référence de projet à un assembly contenant une classe proxy pour un service Web. Pour plus d’informations, consultez [création de Ports Web](../core/creating-web-ports.md).  
  
### <a name="to-remove-a-port-type"></a>Pour supprimer un type de port  
  
-   Dans la fenêtre Vue Orchestration, cliquez sur le type de port à supprimer, puis cliquez sur **supprimer**.  
  
    > [!NOTE]
    >  Si le type de port est utilisé, le fait de le supprimer aura une incidence sur la configuration des ports configurés pour l'utiliser.  
  
    > [!NOTE]
    >  Les éléments apparaissant en lecture seule sont définis dans une autre orchestration.  
  
### <a name="to-set-the-type-modifier-for-a-port-type"></a>Pour définir le modificateur de type d'un type de port  
  
-   Dans la fenêtre Propriétés, définissez la propriété suivante :  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |Modificateur de type|Détermine l'étendue du type de port :<br /><br /> Privé : l'accès à ce type de port est limité au module contenant.<br /><br /> Public : l'accès à ce type de port n'est pas limité.<br /><br /> Interne : l'accès à ce type de port est limité aux modules d'un même projet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de communication](../core/communication-pattern.md)   
 [Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md)   
 [L’utilisation de Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md)