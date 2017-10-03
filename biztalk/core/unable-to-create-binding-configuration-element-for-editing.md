---
title: "Impossible de créer l’élément de configuration de liaison pour la modification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71853662-5a4a-417e-8160-c93dbcbea336
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5c4387e0cb9287ecc4d491291fdfd1fa6b79ab9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unable-to-create-binding-configuration-element-for-editing"></a>Impossible de créer l'élément de configuration de la liaison pour la modification
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Impossible de créer l'élément de configuration de la liaison pour la modification. Vérifiez les valeurs des propriétés BindingType et BindingConfiguration.|  
  
## <a name="explanation"></a>Explication  
 Une erreur s'est produite lors du chargement d'un élément de liaison à des fins d'affichage dans l'interface utilisateur. Cette erreur se produit généralement avec les liaisons personnalisées. L'élément de liaison est probablement manquant dans le fichier de configuration, ce qui explique pourquoi il n'est pas disponible dans la liste déroulante pour la liaison.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez les valeurs de la **BindingType** et **BindingConfiguration** propriétés.  
  
 Pour plus d'informations sur la création des éléments de configuration de liaison, consultez la ressource suivante :  
  
-   [Configuration de l’adaptateur WCF-NetMsmq](../core/configuring-the-wcf-netmsmq-adapter.md)