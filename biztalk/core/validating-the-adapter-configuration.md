---
title: "Validation de la Configuration de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8eeb8742-7083-462b-8d3a-e58103112542
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c03054332e0cd2117c1219afec3dd1aa0a09d6bd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="validating-the-adapter-configuration"></a>Validation de la configuration des adaptateurs
Lors de l’ajout de l’emplacement de réception et le port d’envoi, vous devez configurer les propriétés personnalisées dans le  **\<**  *nom de l’adaptateur*  **\> propriétés du Transport**  boîte de dialogue. Les fichier de schéma XSD du projet AdapterHarness définissent ces propriétés.  
  
 La validation du schéma de configuration s'effectue en trois phases :  
  
1.  Lors de l'affichage d'une configuration enregistrée, l'infrastructure d'adaptateurs valide le document XML enregistré par rapport au schéma avant de charger le document dans la page de propriétés. L'infrastructure suppose qu'un document non valide indique un changement dans la définition du schéma de configuration. Seuls les documents valides sont chargés dans la page de propriétés.  
  
2.  Lors de l’enregistrement d’une configuration, si l’adaptateur implémente les **IAdapterConfigValidation** interface, l’infrastructure transmet à l’adaptateur le document XML construit à partir de la sérialisation des données de la page de propriété. L'adaptateur traite ensuite le document. Les erreurs doivent générer des exceptions qui sont appelées par l'infrastructure et affichées à l'écran de l'utilisateur. Les valeurs manquantes ou générées doivent être générées lors de la validation. À l’aide de la \<browsable show = « false »\> décoration supprime l’affichage d’une entrée dans la grille des propriétés, même si la valeur s’affiche dans l’instance XML.  
  
3.  Si vous enregistrez une configuration avant de placer la valeur dans la base de données, l'infrastructure valide à nouveau le document XML par rapport au schéma. Cela permet de garantir que seules les valeurs valides sont conservées.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de conception de l’adaptateur](../core/adapter-design-issues.md)