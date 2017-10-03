---
title: "Single Sign-On : Événement 10854 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8faed9d-5c7e-4b99-bcd9-ea5f670d5e72
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42f9e9e761689b2ed21ec37acdbb8a63f1f88070
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10854"></a>Single Sign-On : Événement 10854
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10854|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_INVALID_STRING_FORMAT|  
|Texte du message|Le format de chaîne est incorrect pour cette fonction.|  
  
## <a name="explanation"></a>Explication  
 Le format de chaîne est incorrect pour cette fonction.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La mise en forme correcte des chaînes de mot de passe est décrite ci-après :  
  
 Propriété de type VT_BSTR  
  
 Le délimiteur est / (barre oblique)  
  
 sd = situation par défaut (pas d'opération - ne rien faire)  
  
 Exemple : le contrôleur de domaine /  
  
 (aucune modification - « Cat » par « Cat »)  
  
 cm = caractère majuscule  
  
 Exemple : CU /  
  
 (indiquer le mot de passe en majuscules - « Cat » par « CAT »)  
  
 lm = lettres minuscules  
  
 Exemple : lc /  
  
 (indiquer le mot de passe en minuscules - « Cat » par « cat »)  
  
 sc = supprimer des caractères - suivi du nombre, puis des caractères  
  
 Exemple : rc/2 / #@/  
  
 (supprimez les caractères « # » et « @ » du mot de passe - «C@t# » « CT »)  
  
 cr = caractères de remplacement - suivi du nombre, des caractères à remplacer, ainsi que des caractères de remplacement  
  
 Exemple : sc/3/abc/def /  
  
 (supprimer les caractères « a », « b » et « c » du mot de passe et les remplacer par « d », « e » et « f » respectivement)  
  
 (« Cat » par « Cdt »)  
  
 rd = remplir à partir du début - suivi du nombre (longueur minimum du mot de passe) et d'un seul caractère de remplissage  
  
 Exemple : ps/8/Nb /  
  
 (si le mot de passe comprend moins de 8 caractères, remplir à partir du début avec le caractère « # » jusqu'à obtenir un total de 8 caractères)  
  
 (« Cat » par « #####Cat »)  
  
 rf = remplir à partir de la fin - suivi du nombre (longueur minimum du mot de passe) et d'un seul caractère de remplissage  
  
 Exemple : pe/10 / $/  
  
 (si le mot de passe comprend moins de 10 caractères, remplir à partir de la fin avec le caractère « $ » jusqu'à obtenir un total de 10 caractères)  
  
 (« Cat » par « Cat$$$$$$$ »)  
  
 tr = tronquer - longueur limite de la chaîne, suivie du nombre  
  
 Exemple : tr/11 /  
  
 (« Cat123456789 » par « Cat12345678 ») ;  
  
 Les jetons sont traités dans l'ordre dans lequel ils apparaissent dans la chaîne.  
  
 Exemple :  
  
 cm/sc/1/&/ce/2/#$/--/rd/8/&/tr/32/