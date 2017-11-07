---
title: "Problèmes connus avec la génération de schéma et de Validation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df1eaa6c-0d3e-4aec-9de0-8b9817b7bb97
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a462ab04aad857bf87b189cafce14bb9c3747e8
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="known-issues-with-schema-generation-and-validation"></a>Problèmes connus avec la Validation et génération de schéma
Cette rubrique fournit des informations concernant les problèmes connus en matière de génération et de validation de schéma.  
  
## <a name="an-instance-message-generated-for-a-positional-record-with-tags-could-be-incorrect"></a>Un message d'instance généré pour un enregistrement positionnel doté de balises est peut-être incorrect  
 Dans les enregistrements positionnels, la balise peut se trouver dans un champ ou s'étendre entre des champs. Dans les deux cas, l'instance générée ne sera pas valide et provoquera un échec dans le moteur d'analyse au cours de l'étape d'analyse.  
  
 Si la balise ne fait partie d'aucun enfant (enregistrements enfants ou champs enfants), ce problème ne se produira pas.  
  
 Pour résoudre ce problème, incluez la valeur réelle de la balise comme valeur par défaut dans le schéma. Dans l’extension de fichier plat de l’Éditeur BizTalk, vous pouvez définir le **valeur fixe** ou **valeur par défaut** propriété du champ positionnel approprié avec la valeur de la balise.  
  
## <a name="an-instance-message-generated-for-a-field-with-some-restrictions-may-not-pass-validation"></a>Un message d'instance généré pour un champ avec certaines restrictions risque de ne pas être validé  
 Lorsque vous générez un message d’instance à partir d’un schéma qui contient un ou plusieurs **Fieldelement** et **attribut de champ** nœuds qui ont des types de données qui ont été dérivées à l’aide du mécanisme de restriction, comme Lorsque le **modèle** propriété est utilisée, les exemples de données générés pour ces champs n’est peut-être pas conforme aux exigences de la restriction, ce qui empêche la validation réussie de ce message d’instance à l’aide du même schéma à partir de qu’il a été généré.  
  
## <a name="an-instance-message-generated-for-a-schema-that-contains-an-infinite-loop-may-not-be-valid"></a>Un message d'instance généré pour un schéma qui contient une boucle infinie n'est peut-être pas valide  
 Votre schéma peut contenir une boucle infinie lorsqu’elle contient une référence circulaire à un nœud avec un **Min Occurs** valeur supérieure ou égale à un, empêchant essentiellement une condition d’arrêt de la propriété. La génération du message d'instance s'arrêtera artificiellement afin que l'opération de génération puisse se terminer, mais le message d'instance produit ne sera par conséquent pas conforme au schéma à partir duquel il a été généré. Ce type de schéma est généralement suspect.  
  
## <a name="validation-of-xml-instance-fails-for-document-schema-which-has-the-target-namespacehttpwwww3orgxml1998namespace"></a>La validation de l'instance XML a échoué pour le schéma de document dont l'espace de noms cible est « http://www.w3.org/XML/1998/namespace ».  
 Le lien hypertexte « http://www.w3.org/XML/1998/namespace » est un espace de noms réservé dont le préfixe doit être « XML ». Vous pouvez modifier manuellement le préfixe et utiliser « XML ».

## <a name="see-also"></a>Voir aussi
Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
