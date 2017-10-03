---
title: BTAD_SilentMode | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAD_SilentMode [environment variable], about BTAS_SilentMode
- BTAD_SilentMode [environment variable]
- BTAD_SilentMode [environment variable], warnings
ms.assetid: 271835cf-1587-44c5-b5af-b4df4e981ab4
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31715835c98d2f60a3b5f1c18251571ea57641d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btadsilentmode"></a>BTAD_SilentMode
BTAD_SilentMode spécifie des options d'exécution du script en mode silencieux.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous sélectionnez une option de mode silencieux, BTS Installer insère sa valeur dans la variable BTAD_SilentMode.  
  
 La valeur par défaut de BTAD_SilentMode est 2, ce qui indique que le script s'exécute en mode silencieux. Le tableau suivant répertorie les valeurs possibles de BTAD_SilentMode.  
  
> [!CAUTION]
>  Si vous démarrez l'interface utilisateur BizTalk Server à partir de scripts, les boîtes de dialogue modales risquent de ne pas être visibles ou actives, ce qui ne facilite pas leur affichage et leur fermeture. Les bases de données BizTalk risquent de ne plus être accessibles et de se verrouiller lorsque des boîtes de dialogue modales sont ouvertes. C'est pourquoi les scripts destinés à des systèmes de production doivent s'exécuter en mode silencieux.  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Ne modifie pas le niveau de l'interface utilisateur.|  
| 1|Utilise le niveau d'interface utilisateur par défaut.|  
|2|Effectue une installation silencieuse (valeur par défaut).|  
|3|Permet la gestion simple de l'avancement et des erreurs.|  
|4|Fournit une interface utilisateur créée ; supprime les assistants.|  
|0x80|En cas de combinaison avec l'une des valeurs ci-dessus, Windows Installer affiche une boîte de dialogue modale indiquant si le script s'est exécuté correctement ou si une erreur s'est produite. Aucune boîte de dialogue ne s'affiche si l'utilisateur annule l'opération.|  
|0x40|En cas de combinaison avec la valeur 3, Windows Installer affiche des boîtes de dialogue de progression mais aucune boîte de dialogue modale ni aucune boîte de dialogue d'erreur.|  
|0x20|En cas de combinaison avec la valeur 3, Windows Installer affiche des boîtes de dialogue de progression mais aucune boîte de dialogue modale ni aucune boîte de dialogue d'erreur.|  
|0x100|En cas de combinaison avec la valeur 3, Windows Installer affiche des boîtes de dialogue de progression mais aucune boîte de dialogue modale ni aucune boîte de dialogue d'erreur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Variables d’environnement de Script de pré-traitement et de post-traitement](../core/pre-and-post-processing-script-environment-variables.md)   
 [Comment les Variables d’environnement indiquent état du déploiement](../core/how-environment-variables-indicate-deployment-state.md)