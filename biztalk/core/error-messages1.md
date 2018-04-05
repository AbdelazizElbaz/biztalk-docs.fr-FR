---
title: Erreur Messages1 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error messages
ms.assetid: db9c9634-3f4b-4b38-b3ba-388e587fccd8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80a44049c43c499ac05a8a6f296d11add934267a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-messages"></a>Messages d'erreur
Le tableau suivant décrit les messages d'erreur dans le système JD Edwards EnterpriseOne et les corrections possibles.  
  
|ID d'erreur|Cause possible/Description de l'erreur|Correction possible|  
|--------------|-----------------------------------------|-------------------------|  
|E-JDE0027|Fichiers JAR JD Edwards EnterpriseOne manquants. Impossible d'acquérir l'objet de connexion JD Edwards EnterpriseOne.|Vérifiez vos informations d’identification. Vérifiez vos paramètres et informations d'identification CLASSPATH. Reportez-vous à la variable d'environnement.|  
|I-JDE0043|Serveur d'applications, port, environnement, chemin d'accès du fichier de configuration, utilisateur, mot de passe erronés. Échec de la connexion.|Vérifiez vos informations d'identification. Reportez-vous à la variable d'environnement.|  
|I-JDE0048|Si le fichier jdearglist.txt est inexistant ou vide, un message d'information s'affiche dans le journal lors de l'ouverture de l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne.|Mettez à jour le fichier jdearglist.txt pour entrer une liste de paramètres afin qu'ils soient automatiquement alignés à droite et complétés d'espaces à gauche. Pour plus d’informations, consultez [gestion des valeurs de chaîne](../core/handling-string-values2.md). Chaque fois que vous modifiez jdearglist, vous devez régénérer les schémas pour cet objet d'entreprise.|  
|E-JDE0027|Impossible d'acquérir l'objet de connexion JD Edwards EnterpriseOne. Vérifiez votre variable CLASSPATH et vos informations d'identification.|Vérifiez l'emplacement du fichier jdeinterop.ini.|  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md)   
 [Informations techniques de référence](../core/technical-reference6.md)