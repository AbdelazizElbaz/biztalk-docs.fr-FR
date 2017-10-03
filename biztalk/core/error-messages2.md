---
title: Erreur Messages2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error messages, JD Edwards OneWorld adapters
- adapters [JD Edwards OneWorld adapters], error messages
- JD Edwards OneWorld adapters, error messages
ms.assetid: 9fb65d50-83c6-426e-a0d6-674800ecf70f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84b26891592162c553fb270d2d8c9482f1c2b4d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-messages"></a>Messages d'erreur
Le tableau suivant décrit les messages d'erreur dans le système JD Edwards OneWorld et les corrections possibles.  
  
|ID d'erreur|Cause possible/Description de l'erreur|Correction possible|  
|--------------|-----------------------------------------|-------------------------|  
|**E-JDE0002**|Fichiers JAR JD Edwards OneWorld manquants.<br /><br /> Impossible d'instancier l'objet de classe pour JD Edwards OneWorld Java Data Bean.|Vérifiez le chemin d'accès du référentiel.<br /><br /> Pour plus d’informations, consultez [des Types de base](../core/basic-types1.md).|  
|**E-JDE0027**|Fichiers JAR JD Edwards OneWorld manquants. Impossible d'acquérir l'objet de connexion JD Edwards OneWorld.|Vérifiez votre variable d'environnement CLASSPATH.<br /><br /> Consultez la rubrique Mise à jour de CLASSPATH.<br /><br /> Vérifiez vos informations d’identification.<br /><br /> Pour plus d’informations, consultez [des Types de base](../core/basic-types1.md).|  
||Fichiers JAR JD Edwards OneWorld manquants.<br /><br /> Chemin d'accès du référentiel erroné.|Vérifiez l’emplacement du fichier jdeinterop.ini. Vérifiez le chemin d’accès du référentiel défini dans le fichier jdeinterop.ini.<br /><br /> Lors de l'importation d'un processus d'entreprise JD Edwards OneWorld sur un autre ordinateur, vous devez copier jdeinterop.ini manuellement.|  
||Impossible d'acquérir l'objet de connexion JD Edwards OneWorld.|Vérifiez les paramètres de chemin de classe et les informations d’identification d’ouverture de session...|  
|**I-JDE0043**|Serveur d'applications, port, environnement, chemin d'accès du fichier de configuration, utilisateur, mot de passe erronés.<br /><br /> Échec de l’ouverture de session.|Vérifiez vos informations d’identification d’ouverture de session.<br /><br /> Pour plus d’informations, consultez [des Types de base](../core/basic-types1.md).|  
|**I-JDE0048**|Si le fichier jdearglist.txt est inexistant ou vide, un message d'information s'affiche dans le journal lors de l'ouverture de l'adaptateur BizTalk pour JD Edwards OneWorld.|Mettez à jour le fichier jdearglist.txt pour entrer une liste de paramètres afin qu'ils soient automatiquement alignés à droite et complétés d'espaces à gauche.<br /><br /> Consultez [la gestion des valeurs de chaîne](../core/handling-string-values1.md).<br /><br /> Chaque fois que vous modifiez jdearglist, vous devez régénérer les schémas pour cet objet d'entreprise.|  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : les Types de données](../core/appendix-a-data-types.md)   
 [Résolution des problèmes de JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)