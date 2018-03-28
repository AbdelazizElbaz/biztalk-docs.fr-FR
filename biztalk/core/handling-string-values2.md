---
title: La gestion des chaînes Values2 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- string values, configuring
- formatting strings
- strings, formatting
- left-justified string values
- jdearglist.txt
- strings, left-justified
- right-justified string values
- strings, right-justified
ms.assetid: 23d54731-b2b9-4610-a533-e041237e0bb3
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 024663faa56d92361d861a61a0d64a4608839aa6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="handling-string-values"></a>Gestion des valeurs de chaîne
Cette rubrique décrit la configuration de certains arguments de chaîne comme alignés à droite (et remplis à gauche).  
  
## <a name="types-of-string-values"></a>Types de valeurs de chaîne  
 JD Edwards EnterpriseOne expose deux types de valeurs de chaîne via sa couche d'interopérabilité :  
  
-   Char : un caractère unique  
  
-   chaîne de longueur maximale  
  
 JD Edwards EnterpriseOne utilise la notation hongroise pour nommer les arguments de ces types dans les fonctions d'entreprise. Par exemple, les arguments de ces types commencent par :  
  
-   c  
  
-   sz  
  
### <a name="left-justified-values"></a>Valeurs alignées à gauche  
 JD Edwards EnterpriseOne attend une valeur alignée à gauche pour une majorité d'arguments de type sz, la chaîne de longueur maximale ou le tableau de caractères. Par exemple, pour une ligne « Adresse de domicile » d'une longueur maximale de 40, JD Edwards EnterpriseOne attend ce qui suit :  
  
 « 4567 rue. »  
  
 chaîne complétée d'espaces pour atteindre la longueur de 40 caractères. Il n'est pas nécessaire d'entrer le remplissage car l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne le fait automatiquement. Vous devez juste saisir « 4567 Rue Pr » dans le code client.  
  
### <a name="right-justified-values"></a>Valeurs alignées à droite  
 Pour certains sous-ensembles de valeurs de ce type, JD Edwards EnterpriseOne attend des valeurs alignées à droite, avec un remplissage à gauche. Par exemple, pour les fonctions du module source B4200310, l’argument szBusinessUnit est de longueur 12. Cet argument représente une usine, par exemple une installation de production. Pour un numéro d'usine de 30, JD Edwards EnterpriseOne attend la valeur suivante :  
  
 "           30"  
  
 Pour entrer une valeur qui sera aligné à droite, vous devez entrer le paramètre dans un fichier nommé jdearglist.txt. Ce dernier est lu lorsque vous générez le schéma. Chaque valeur de ce fichier texte est automatiquement convertie en une valeur alignée à droite et remplie à gauche avec des espaces vides.  
  
 Vous devez créer le fichier jdearglist.txt à l'aide d'un éditeur de texte, avec des entrées décrivant ces paramètres, puis l'enregistrer dans le dossier suivant :  
  
 C:\Program Files\Microsoft BizTalk Adapters\JDEEnterpriseOne\config  
  
 Si ce fichier n'existe pas ou est vide, un message est affiché dans le journal de l'adaptateur BizTalk pour JD Edwards EnterpriseOne lors de la première ouverture de l'adaptateur.  
  
> [!NOTE]
>  Si vous modifiez ce fichier après avoir généré votre schéma, vous devez régénérer le schéma pour actualiser les données qu'il contient. Pour vérifier que vous utilisez les dernières informations de ce fichier, vous pouvez utiliser le Gestionnaire des tâches pour arrêter le processus browsingagent.exe avant de générer de nouveau votre schéma. Toutefois, cela ne devrait pas être nécessaire.  
  
 Voici un exemple du format des entrées dans le fichier jdearglist.txt :  
  
```  
<SourceModule>.<BusinessFunction>.<Argument>  
  
```  
  
 Par exemple :  
  
```  
B4200310.F4211FSBeginDoc.szBusinessUnit  
```  
  
 Pour un ensemble de fonctions commerciales appartenant au même module commercial, des arguments de nom similaire (du même type) sont partagés entre plusieurs ou toutes les fonctions commerciales. Vous pouvez utiliser le caractère générique astérisque (*) au lieu du nom de fonction commerciale. Par exemple :  
  
```  
B4200310.*.szBusinessUnit  
  
```  
  
> [!NOTE]
>  Lors de l'importation d'un processus d'entreprise JD Edwards EnterpriseOne sur un autre ordinateur, vous devez copier jdearglist.txt manuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe B : Types de données](../core/appendix-b-data-types.md)