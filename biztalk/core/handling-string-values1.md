---
title: "La gestion des chaînes Values1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jdearglist.txt, configuring strings
- strings, left-justified
- strings, configuring
- strings, right-justified
ms.assetid: a180b818-1009-45f5-a503-d10ed7dd27fc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f32b29b9a8688fe8402730c1db8f12e42a67bab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-string-values"></a>Gestion des valeurs de chaîne
Cette rubrique décrit la configuration de certains arguments de chaîne comme alignés à droite (et remplis à gauche).  
  
## <a name="types-of-string-values"></a>Types de valeurs de chaîne  
 JD Edwards OneWorld expose deux types de valeurs de chaîne à l'aide de sa couche d'interopérabilité :  
  
-   Char : un caractère unique  
  
-   chaîne de longueur maximale  
  
 JD Edwards OneWorld utilise une notation hongroise pour nommer les arguments de ces types dans les fonctions commerciales. Par exemple, les arguments de ces types commencent par :  
  
-   c  
  
-   sz  
  
### <a name="left-justified-values"></a>Valeurs alignées à gauche  
 Pour une majorité d'arguments de type sz, la chaîne de longueur maximale ou tableau de caractères, JD Edwards OneWorld attend une valeur alignée à gauche. Pour une ligne d'adresse, dont la longueur maximale est de 40 caractères, JD Edwards OneWorld attend (par exemple) :  
  
 "4567 Main St.       "  
  
 chaîne complétée d'espaces pour atteindre la longueur de 40 caractères. Il n'est pas nécessaire d'entrer les caractères de remplissage, car l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld le fait automatiquement. Vous devez uniquement entrer « 4567 Main St.» , dans votre code client.  
  
### <a name="right-justified-values"></a>Valeurs alignées à droite  
 Pour certains sous-ensembles de valeurs en relation avec ce type, JD Edwards OneWorld attend des valeurs alignées à droites avec un remplissage à gauche. Par exemple, pour les fonctions du module source B4200310, l’argument szBusinessUnit est de longueur 12. Cet argument représente une usine, par exemple une installation de production. Pour un numéro d’unité 30, J.D. Edwards OneWorld XE attend une valeur de :  
  
 "          30"  
  
 Pour entrer une valeur qui sera aligné à droite, vous devez entrer le paramètre dans un fichier nommé jdearglist.txt. Ce dernier est lu lorsque vous générez le schéma. Toute valeur répertoriée dans ce fichier texte est automatiquement convertie en une valeur alignée à droite et complétée d'espaces à gauche.  
  
 Vous devez créer jdearglist.txt à l’aide d’un texte de l’éditeur, avec des entrées décrivant ces paramètres et enregistrez-le dans le dossier suivant : %BizTalk_Install_Adapter%\config\JDE\  
  
 Où **BizTalk_Install_Adapter %** est le répertoire dans lequel vous avez installé l’adaptateur BizTalk pour JD Edwards OneWorld.  
  
 Si ce fichier est inexistant ou vide, un message d'information s'affiche dans l'adaptateur BizTalk pour le journal JD Edwards OneWorld lors de la première ouverture de l'adaptateur.  
  
> [!NOTE]
>  Si vous modifiez ce fichier après avoir généré votre schéma, vous devez régénérer le schéma pour actualiser les données qu'il contient.  
  
 Pour vérifier que vous utilisez les dernières informations de ce fichier, vous pouvez utiliser le Gestionnaire des tâches pour arrêter le processus browsingagent.exe avant de générer de nouveau votre schéma. Toutefois, cela ne devrait pas être nécessaire.  
  
 Voici un exemple du format des entrées dans le fichier jdearglist.txt :  
  
```  
<SourceModule>.<BusinessFunction>.<Argument>  
```  
  
 Exemple :  
  
```  
B4200310.F4211FSBeginDoc.szBusinessUnit  
```  
  
 Pour un ensemble de fonctions commerciales appartenant au même module commercial, des arguments de nom similaire (du même type) sont partagés entre plusieurs ou toutes les fonctions commerciales. Vous pouvez utiliser le caractère générique astérisque (*) au lieu du nom de fonction commerciale. Exemple :  
  
```  
B4200310.*.szBusinessUnit  
```  
  
> [!NOTE]
>  Lors de l'importation d'un processus d'entreprise JD Edwards OneWorld sur un autre ordinateur, vous devez copier jdearglist.txt manuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètre Justification des chaînes dans Jdearglist](../core/setting-string-justification-in-jdearglist.md)   
 [Annexe a : les Types de données](../core/appendix-a-data-types.md)