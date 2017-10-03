---
title: "Codes d’erreur SWIFT dans BizTalk Server | Documents Microsoft"
description: "Afficher les types de classe et de validation pour l’accélérateur SWIFT dans BizTalk Server"
ms.custom: 
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03699986-965b-4a28-ab2e-09f110fb4db6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6d8e027eb9cce1cf66342484070310141e10b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-error-codes"></a>Codes d’erreur SWIFT
SWIFT définit plusieurs validations imposées par le réseau à l’ensemble des messages d’analyse (FIN). Chaque validation est liée à un type de contrôle sur le contenu du message et est associée à un code d’erreur de trois caractères. Le premier caractère du code d’erreur implique la classe du problème détecté et est une lettre. Les deux caractères restants indiquent les détails de l’erreur (lorsqu’elles sont combinées avec la classe) et apparaissent toujours sous forme de code à deux chiffres.  

## <a name="class-of-errors"></a>Classe d’erreurs  
 Le tableau suivant répertorie les désignations de lettre, un type de validation, modification de la règle associée à chaque classe d’erreur, et indique si la classe d’erreur est pris en charge.  
  
|Classe|Modification de type et de la règle de validation|Pris en charge ?|  
|-----------|-------------------------------------|----------------|  
|**C, D, E**|Règles de validation sémantique 0-299|Pris en charge|  
|**Knn**|Mot de code non valide dans le champ*nn*|Pris en charge|  
|**M50**|Longueur du message dépassée|Non pris en charge|  
|**M60**|Caractère non-SWIFT rencontré|Pris en charge|  
|**T**|Codes d’erreur de validation de texte|Pris en charge|  
|**G**|Codes d’erreur spécifiques pour les règles de message utilisateur groupe (Chope) Textval|Non pris en charge|  
|**B**|Codes d’erreur spéciale pour les services à valeur ajoutée|Non pris en charge|  
  
 Toutes les erreurs SWIFT doivent être référencées dans la *SWIFT utilisateur manuel*. Pour plus d’informations et pour obtenir la liste complète des codes d’erreur SWIFT, reportez-vous à la *règles de Validation du Format de Message* volume de la *SWIFT utilisateur manuel*. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]implémente les règles dans l’édition de septembre 2003 de cette publication. Vous pouvez accéder au site Web de SWIFT [http://go.microsoft.com/fwlink/?LinkId=27885](http://go.microsoft.com/fwlink/?LinkId=27885).  

## <a name="validation-errors"></a>Erreurs de validation  
 Il existe certains codes qui sont définis par A4SWIFT. Ces codes d’erreur sont utilisées dans les règles de validation/par réseau créée et implémentée par A4SWIFT, il n’existe aucun code d’erreur correspondant défini par SWIFT pour ces règles. Tableau ci-dessous montre le code d’erreur et le cas correspondant dans lequel l’erreur est levée. est le champ particulier qui lève l’erreur.  
  
|Code d'erreur| Description|  
|----------------|-----------------|  
|A4SWIFT001|Le premier caractère du champ multiligne ne peut pas être ' :' ou '-' caractère pour le deuxième et les lignes suivantes.|  
|A4SWIFT002|Champ contient une valeur non valide.|  
  
> [!NOTE]
>  [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]prend en charge certains messages hérités, étant donné que les applications internes peuvent utiliser ces messages. Par conséquent, A4SWIFT gère les règles SWIFT associées et les codes d’erreur.

## <a name="more-good-info"></a>Plus d’informations correct
[Résolution des problèmes : Problèmes et résolutions](troubleshooting-issues-and-resolutions1.md)  
[Problèmes connus](known-issues5.md)  
[Commun des termes et définitions](glossary6.md)