---
title: Nœud BindingInfo | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BindingInfo node [binding file]
ms.assetid: a71d100c-cf8b-4a54-b239-ee0ca2d8148c
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dc15cbfe4bb3a98e17a894c5a763c0ca18bdcb3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bindinginfo-node"></a>Nœud BindingInfo
Le **BindingInfo** nœud d’un fichier de liaison est le nœud racine d’un fichier de liaison et contient des informations qui s’applique à toutes les entrées dans le fichier de liaison, ainsi que des informations sur le serveur BizTalk Server que le fichier de liaison a été exporté. De.  
  
## <a name="nodes-in-the-bindinginfo-node"></a>Nœuds du nœud BindingInfo  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Assembly|Attribut|xs:string|Indique les informations pour la dll Microsoft.BizTalk.Deployment utilisée lors de la création du fichier de liaison. Inclut les attributs Version, Culture et PublicKeyToken séparés par des virgules pour cet assembly.|Requis|Valeur par défaut : **« Microsoft.BizTalk.Deployment, Version = 3.0.1.0, Culture = neutral, PublicKeyToken = 31bf3856ad364e35 »**|  
|Version|Attribut|xs:string|Indique la version de BizTalk Server dans laquelle le fichier de liaison a été généré.|Requis|Valeur par défaut : **3.5.1.0**|  
|BindingStatus|Attribut|BindingState (SimpleType)|Indique l'état de liaison des artefacts exportés avec le fichier de liaison.|Requis|Valeur par défaut : Aucun<br /><br /> Valeurs valides :<br /><br /> -Inconnu<br />-NoBindings<br />-Indépendant<br />-PartiallyBound<br />-FullyBound|  
|BoundEndpoints|Attribut|xs:int|Indique le nombre de points de terminaison liés dans le fichier de liaison.|Requis|Valeur par défaut : **0**|  
|TotalEndpoints|Attribut|xs:int|Indique le nombre total de points de terminaison dans le fichier de liaison.|Requis|Valeur par défaut : **0**|  
| Description|Élément|xs:string|Spécifie une description textuelle de la section BindingInfo du fichier de liaison.|Facultatif|Valeur par défaut : vide|  
|Horodateur|Élément|xs:dateTime|Indique à quel moment le fichier de liaison a été exporté.|Requis|Valeur par défaut : heure sur le serveur BizTalk à laquelle le fichier de liaison a été exporté.|  
|[Nœud ModuleRefCollection](../core/modulerefcollection-node.md)|Record|ArrayOfModuleRef (ComplexType)|Nœud conteneur pour les assemblys .NET exportés avec le fichier de liaison.|Facultatif|Valeur par défaut : Aucun|  
|[Nœud SendPortCollection](../core/sendportcollection-node.md)|Record|ArrayOfSendPort (ComplexType)|Nœud conteneur pour les ports d'envoi exportés avec le fichier de liaison.|Facultatif|Valeur par défaut : Aucun|  
|[Nœud DistributionListCollection](../core/distributionlistcollection-node.md)|Record|ArrayOfDistributionList (ComplexType)|Nœud conteneur pour les listes de distribution exportées avec le fichier de liaison.|Facultatif|Valeur par défaut : Aucun|  
|[Nœud ReceivePortCollection](../core/receiveportcollection-node.md)|Record|ArrayOfReceivePort (ComplexType)|Nœud conteneur pour les ports de réception exportés avec le fichier de liaison.|Facultatif|Valeur par défaut : Aucun|  
  
 Le code suivant présente le format du XML utilisé dans le nœud BindingInfo d'un fichier de liaison :  
  
```  
<BindingInfo xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
Assembly="Microsoft.BizTalk.Deployment, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
Version="3.5.1.0" BindingStatus="FullyBound"   
BoundEndpoints="12"   
TotalEndpoints="12">  
<Description/>  
<Timestamp>2005-08-23T16:27:40.5948205-07:00</Timestamp>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des fichiers de liaison](../core/customizing-binding-files.md)