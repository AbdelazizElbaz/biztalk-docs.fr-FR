---
title: "ID de nœud de métadonnées pour l’adaptateur Siebel dans le Pack d’adaptateurs BizTalk | Documents Microsoft"
description: "Métadonnées, search, les types de nœuds de récupération et les identificateurs utilisés dans les composants Siebel qui sont exposés dans l’adaptateur Siebel - Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdffc8d1-0a0a-48d7-b134-5d16acf2c523
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5aecf8995b30f5cd545e4202da0c468d730e277
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="node-types-and-ids-for-the-siebel-adapter"></a>Types de nœuds et ID de l’adaptateur Siebel

## <a name="metadata-node-types-and-ids"></a>Types de nœuds de métadonnées et des ID 
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] met en évidence des artefacts du système Siebel de façon hiérarchique. Le tableau suivant décrit les types de nœuds et l’ID de nœud pour les artefacts Siebel exposés par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
|Artefact|Type de nœud|Id de nœud|Exemple| Description|  
|--------------|---------------|-------------|-------------|-----------------|  
|Objets métier (tous les objets métier)|CATÉGORIE|[VERSION] / BusinessObjects|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects|Retourne tous les objets métier.|  
|Objet métier (BO)|CATÉGORIE|[VERSION] /BusinessObjects/ [BO]|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account|Retourne tous les composants d’entreprise associés à l’objet métier spécifié.|  
|Composant d’entreprise (BC)|CATÉGORIE|[VERSION] /BusinessObjects/ [BO] / [BC]|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account|Retourne toutes les opérations associées au composant métier spécifiée.|  
|Insert|OPERATION|[VERSION] /BusinessObjects/ [BO] / [BC] / insertion|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/INSERT|Retourne l’opération d’insertion pour le composant de gestion spécifié.|  
|Requête|OPERATION|[VERSION] /BusinessObjects/ [BO] / [BC] / requête|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Query|Retourne l’opération de requête pour le composant de gestion spécifié.|  
|Update|OPERATION|[VERSION] /BusinessObjects/ [BO] / [BC] / mise à jour|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Update|Retourne l’opération de mise à jour pour le composant de gestion spécifié.|  
|DELETE|OPERATION|[VERSION] /BusinessObjects/ [BO] / [BC] / Delete|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete|Retourne l’opération de suppression pour le composant de gestion spécifié.|  
|Associer|OPERATION|[VERSION] /BusinessObjects/ [BO] / [BC] / associer|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Associate|Retourne l’opération d’association pour le composant de gestion spécifié.|  
|Dissocier|OPERATION|[VERSION] /BusinessObjects/ [BO] / [BC] / dissocier|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Dissociate|Retourne l’opération recréez-la pour le composant de gestion spécifié.|  
|Query_ [composant d’entreprise multiples enfants]|OPERATION|[VERSION] /BusinessObjects/ [BO] / [BC] / Query_ [composant d’entreprise multiples enfants]|http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Query_Contact|Retourne l’opération de requête pour le composant d’activité enfant|  
|Services professionnels|CATÉGORIE|[VERSION] / BusinessServices|http://Microsoft.LobServices.Siebel/2007/03/BusinessServices|Retourne tous les services professionnels.|  
|Service d’entreprise|CATÉGORIE|[VERSION] /BusinessServices/ [Service d’entreprise]|http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/ATP|Retourne toutes les méthodes d’entreprise pour le service d’activité spécifié.|  
|Méthode de Service d’entreprise|OPERATION|[VERSION] /BusinessServices/ [Service métier] / [méthode de Service d’entreprise]|http://Microsoft.LobServices.Siebel/2007/03/BusinessServices/ATP/ATPRunCheck|Retourne la méthode de service métier spécifiée.|  
  
 [VERSION] = la chaîne de version ; par exemple http://Microsoft.LobServices.Siebel/2007/03.  
  
 [BO] = Siebel d’un objet d’entreprise ; par exemple, le compte.  
  
 [BC] = un composant d’entreprise ; par exemple, le compte.  
  
 [Business Service] = A Siebel business service ; par exemple, DAV.  
  
 [Méthode de Service business] = une méthode d’un service d’entreprise ; par exemple, DismissAlarm.  
  
 [Composant d’entreprise multiples enfants] = un composant d’entreprise à valeurs multiples groupe enfant ; par exemple, le Contact.  
  
## <a name="metadata-search-and-node-ids"></a>Recherche de métadonnées et les ID de nœud  
 Recherche de métadonnées est une puissante fonctionnalité le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] surfaces dans le cadre de son **MetadataRetrievalContract** interface. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] tire parti de cette fonctionnalité pour prendre en charge la recherche les artefacts Siebel suivants.  
  
|Artefact|Id de nœud| Description|  
|--------------|-------------|-----------------|  
|Objet métier|[VERSION] / BusinessObjects|Retourner des objets métier qui correspondent à l’expression de recherche.|  
|Composant d’entreprise|[VERSION] /BusinessObjects/ [BO]|Retourne les composants d’entreprise qui correspondent à l’expression de recherche.|  
|Service d’entreprise|[VERSION] / BusinessServices|Retourner les services métier qui correspond à l’expression de recherche.|  
|Méthode de Service d’entreprise|[VERSION] /BusinessServices/ [Service d’entreprise]|Retourne les méthodes de service d’entreprise qui correspondent à l’expression de recherche.|  
  
 [VERSION] = la chaîne de version ; par exemple http://Microsoft.LobServices.Siebel/2007/03.  
  
 [BO] = un objet d’entreprise Siebel ; par exemple, le compte.  
  
 [Business Service] = un Service d’entreprise Siebel ; par exemple, DAV.  
  
 Pour les expressions de recherche valides, consultez la documentation de Siebel.  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend uniquement en charge la recherche au niveau sous le nœud actuellement sélectionné.  Par exemple, lorsque BusinessObjects est sélectionnée, A * est prise en charge recherche, mais A\*/A\* n’est pas.  
  
## <a name="metadata-retrieval-and-node-ids"></a>Récupération de métadonnées et les ID de nœud  
 L’adaptateur Siebel capture les caractéristiques suivantes pour chaque type d’artefact.  
  
|Artefact|Caractéristiques des métadonnées|  
|--------------|------------------------------|  
|Composant d’entreprise|<ul><li>Nom du composant métier</li><li>Des noms de champ de composant</li><li>Mappage des types de données de champ de composant métier sur les types de WSDL de simples et complexes</li><li>Longueur de champ de composant entreprise mappée à la facette maxLength</li><li>Champ obligatoire du composant entreprise mappé à la facette minOccurs = 1</li><li>Champ facultatif sur le composant entreprise mappé à la facette minOccurs = 0</li><li>Champ de liste de sélection de composant entreprise mappé à un type complex de la liste de choix dans WSDL</li><li>Entreprise composant statique limitées pour contenir une liste énumérée des valeurs de liste de choix</li><li>Contrainte NULL d’entreprise composant champ mappé à la facette isNillable = true</li><li>Opérations de composants d’entreprise<br /><br /> <ul><li>INSERT</li><li>QUERY</li><li>UPDATE</li><li>DELETE</li><li>ASSOCIER</li><li>DISSOCIER</li><li>QUERY_ [Business enfant multiples Comp] pour chaque composant d’entreprise enfant avec lequel le composant de gestion a une relation m : n</li></ul></li></ul>|  
|Méthode de Service d’entreprise|-Nom du Service business<br />-Nom de la méthode<br />-La méthode est l’opération<br />-Les noms de paramètres (méthode)<br />-Types de données de paramètres de méthode mappés aux types de WSDL<br />-Direction du paramètre méthode mappée à la direction du paramètre WSDL<br />-L’ordre des paramètres de méthode mappé à la séquence d’éléments|  
  
 Pour plus d’informations sur le format des métadonnées qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose pour les artefacts et les opérations sur le système Siebel, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).  
  