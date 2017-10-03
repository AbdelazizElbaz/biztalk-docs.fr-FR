---
title: "Dépannage de Questions et réponses | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2f89d92-0a97-4017-8b8e-6afd8b20eaf4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37e63f8838dea7adee91b5b43b2bc881cb53eae1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="general-troubleshooting-questions-and-answers"></a>Questions et réponses d'ordre général sur le dépannage
Les questions/réponses de cette rubrique vous aideront à résoudre les problèmes que vous pouvez rencontrer avec le Mappeur BizTalk.  
  
## <a name="how-do-i-specify-xslt-output-settings"></a>Comment spécifier les paramètres de sortie XSLT ?  
 Vous pouvez utiliser le Mappeur BizTalk pour incluent ou ignorent les déclarations XML et contrôler l’encodage utilisé pour les données d’instance de sortie.  
  
#### <a name="include-or-exclude-an-xml-declaration"></a>Inclure ou exclure une déclaration XML  
  
1.  Dans la vue Grille, cliquez sur la grille du Mappeur. Le **propriétés** fenêtre affiche les propriétés de la grille.  
  
2.  Dans la liste déroulante pour le **omettre la déclaration XML** propriété, sélectionnez **Oui** pour omettre une déclaration XML, ou sélectionnez **non** pour ne pas omettre une déclaration XML.  
  
#### <a name="set-encoding-for-output-instance-data"></a>Définir le codage de données d’instance de sortie  
  
1.  Dans la vue Grille, cliquez sur la grille du Mappeur. Le **propriétés** fenêtre affiche les propriétés de la grille.  
  
2.  Dans la liste déroulante pour le **codage XSLT** propriété, sélectionnez le jeu de caractères vous souhaitez utiliser pour les données d’instance de sortie.  
  
## <a name="how-do-i-create-multipart-mappings"></a>Comment créer des mappages à parties multiples ?  
 Si vous avez plusieurs mappages sont utilisés ensemble, vous devez les associer dans une orchestration à l’aide de la **transformer** forme pour les tester ensemble. Le Mappeur BizTalk ne peut tester qu'un seul mappage à la fois.  
  
## <a name="why-isnt-my-database-functoid-working"></a>Le fonctoid de base de données ne fonctionne pas. Pourquoi ?  
 Les fonctoids de base de données **recherche de base de données** et **extracteur de valeur** ne retournent pas directement les informations sur les erreurs au lieu de cela, de capturer les informations et de fournir à la **retourd’erreur** fonctoid pour une utilisation par votre carte. Vous pouvez utiliser la **retour d’erreur** fonctoid pour la détection d’erreur dans les cas suivants :  
  
-   Lorsque votre mappage comporte un **recherche de base de données** ou **extracteur de valeur** fonctoid qui se comporte pas comme prévu. Pour afficher le message d'erreur, mappez temporairement le fonctoid à un champ du schéma de sortie.  
  
-   Si votre application attend un contenu de message différent lors de l'échec des opérations de la base de données. Vous pouvez utiliser la **retour d’erreur** fonctoid pour détecter une erreur et mapper le message d’erreur à une autre structure pour que les applications en aval puissent réagir de manière contrôlée.  
  
 Pour éviter les erreurs soient détectées qu’au moment de l’exécution, assurez-vous que le premier paramètre de la **retour d’erreur** fonctoid est le résultat d’une **recherche de base de données** fonctoid et non de la sortie d’un autre fonctoid dans la Catégorie de la base de données.  
  
 Pour plus d’informations sur l’utilisation de la **retour d’erreur** fonctoid (y compris un exemple), consultez le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="why-is-my-map-failing-when-calling-my-custom-functoid"></a>Mon mappage ne parvient pas à appeler un fonctoid personnalisé. Pourquoi ?  
 Vous devez installer les fonctoids personnalisés dans le GAC (Global Assembly Cache) sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour qu'un mappage puisse les appeler. Vérifiez que l'assembly contenant votre fonctoid personnalisé a bien été signé et placé dans le GAC. Copiez également l'assembly dans le dossier « %BTSINSTALLPATH%\Developer Tools\Mapper Extensions ».  
  
 Pour plus d’informations sur l’installation des assemblys dans le GAC, consultez [Installation de l’Assembly dans le GAC](../core/assembly-installation-in-the-gac.md). Pour afficher les assemblys installés dans le GAC, ouvrez le dossier des assemblys du répertoire d'installation de votre [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de mappages](../core/troubleshooting-maps.md)