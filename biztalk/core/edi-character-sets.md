---
title: "Jeux de caractères EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57fae748-d66e-4ecf-be00-70147078ef93
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 108424cf9ef8670340e51a1c9747f42eec9cc4cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-character-sets"></a>Jeux de caractères EDI
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise un jeu de caractères pour valider l'intégralité d'un échange EDI. Les jeux de caractères utilisés pour un message X12 et un message EDIFACT ou KEDIFACT sont déterminés de différentes façons.  
  
## <a name="edifact-character-set"></a>Jeu de caractères EDIFACT  
 Un échange EDIFACT décrit lui-même son jeu de caractères. L'élément de données UNB1 est utilisé. EDIFACT requiert que les noms de balise et les délimiteurs/séparateurs soient de type ASCII. Par conséquent, il est possible d'identifier UNB1 pour appliquer la page de codes appropriée au reste de l'échange.  
  
 Lors du traitement d'un message EDIFACT entrant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine le jeu de caractères à utiliser pour ce message à partir de l'élément de données UNB1. Aucun paramètre de l'accord de partenariat commercial n'est nécessaire.  
  
 Lors du traitement d'un message EDIFACT sortant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le jeu de caractères dans l'accord de partenariat commercial ou l'accord de secours. Vous définissez l’élément de données UNB1 dans les **jeu de caractères et séparateurs** page dans les onglets d’accord bidirectionnel (si un accord est défini) ou le **jeu de caractères et séparateurs** page dans l’onglet d’accord de la **Paramètres de secours EDIFACT** boîte de dialogue (si aucun accord n’est défini). UNB1.1 est un élément de données composites obligatoire appelé identificateur de syntaxe. UNB1.2 est la version du jeu de caractères EDIFACT. L'élément de données UNB1 est également utilisé pour valider les valeurs entrées pour les propriétés dans l'interface utilisateur de gestion des partenaires commerciaux, lorsque le jeu de propriétés entier est enregistré (ce n'est pas le cas lorsque vous changez de champ ou affichez une autre page).  
  
 Les jeux de caractères disponibles sont KECA, UNOA, UNOB, UNOC, UNOD, UNOE, UNOF, UNOG, UNOH, UNOI, UNOJ, UNOK, UNOX et UNOY. La valeur par défaut est UNOB. Le jeu de caractères complet pour ces niveaux est spécifié dans les règles de syntaxe EDIFACT ISO 9735.  
  
> [!NOTE]
>  Si le jeu de caractères UNOC est rencontré dans un échange entrant ou sortant, le Désassembleur EDI ou l'Assembleur EDI utilise la page de codes Latin-1, plutôt que la page de codes UTF-8. En effet, UTF-8 n'est pas un sur-ensemble d'UNOC. Certains caractères acceptables dans UNOC provoquent la suspension d'un échange si celui-ci est traité avec la page de codes UTF-8.  
  
 Les caractères des jeux de caractères EDIFACT peuvent être codés sur deux octets ou sur un octet. Pour cette raison, lorsque vous définissez les critères de déclenchement des lots sur la base du nombre de caractères dans l'échange, le nombre d'octets dans l'échange peut varier selon le jeu de caractères utilisé.  
  
 Le segment UNA et le nom de segment UNB sont limités aux valeurs du jeu de caractères ASCII.  
  
## <a name="kedifact-character-set"></a>Jeu de caractères KEDIFACT  
 Comme pour EDIFACT, le jeu de caractères d'un échange KEDIFACT est établi dans l'élément de données UNB1. Comme pour EDIFACT, le jeu de caractères à appliquer par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lorsque le traitement d’un échange KEDIFACT est établi dans l’élément de données **UNB1** de **jeu de caractères et séparateurs** page dans le bidirectionnelles les onglets d’accord (si un accord est défini) ou le **jeu de caractères et séparateurs** page dans l’onglet d’accord de la **paramètres de secours EDIFACT** boîte de dialogue (si aucun accord n’est défini). La valeur de la **identificateur (UNB1.1)** élément doit être défini sur KECA.  
  
## <a name="x12-character-set"></a>Jeu de caractères X12  
 Lorsque le pipeline de réception ou le pipeline d'envoi BizTalk effectue la validation EDI d'un message X12, il utilise le jeu de caractères X12 sélectionné dans sa propriété CharacterSet. Pour définir cette propriété, ouvrez la boîte de dialogue Propriétés pour l'emplacement de réception ou le port d'envoi, cliquez sur le bouton représentant des points de suspension (...) en regard du pipeline d'envoi ou de réception, puis définissez la propriété CharacterSet du Désassembleur ou de l'Assembleur.  
  
 La propriété CharacterSet du pipeline est utilisée pour valider un échange X12 car, contrairement à EDIFACT ou KEDIFACT, un échange X12 ne décrit pas lui-même son jeu de caractères. Selon que l'en-tête ISA est lu avec le codage ISO ou UTF, la recherche de l'accord peut générer différentes valeurs. BizTalk doit donc connaître le jeu de caractères à utiliser pour le traitement du message avant de rechercher l'accord (qui lui permettrait d'obtenir le jeu de caractères applicable à l'accord).  
  
 Vous spécifiez le X12 de caractères à utiliser pour la validation de contrat dans le dans les **jeu de caractères et séparateurs** page dans les onglets d’accord bidirectionnel (si un accord est défini) ou le **jeu de caractères et séparateurs**page sous l’onglet d’accord de secours de la **X12 paramètres de secours** boîte de dialogue (si aucun accord n’est défini). BizTalk utilise uniquement ces paramètres pour valider les valeurs entrées pour les propriétés correspondantes lorsque le jeu de propriétés entier est enregistré (ce n'est pas le cas lorsque vous changez de champ ou affichez une autre page). Le pipeline de réception ou d'envoi ignore ces propriétés de jeu de caractères.  
  
> [!NOTE]
>  Si le jeu de caractères spécifié dans l'accord ou l'accord de secours ne correspond pas au jeu de caractères sélectionné pour le pipeline de réception ou d'envoi, des erreurs de validation du message peuvent survenir. C'est le cas par exemple si la propriété du jeu de caractères X12 dans l'accord est définie sur Extended alors qu'elle est définie sur Basic dans les propriétés du pipeline.  
  
 Les jeux de caractères disponibles sont Basic, Extended (comme décrit dans les guides de spécification/d'implémentation X12) et UTF8/Unicode. Le jeu de caractères par défaut est UTF8.  
  
> [!NOTE]
>  Les valeurs entrées pour le séparateur d'éléments de données, le séparateur d'éléments composites et le terminateur de segment dans l'accord bidirectionnel ou l'accord de secours sont limitées aux valeurs du jeu de caractères ASCII. Ces propriétés ne sont pas validées par rapport au jeu de caractères X12.  
  
 Le jeu de caractères de base inclut le suivantes des lettres majuscules, chiffres, espace et des caractères spéciaux : A à Z, 0 à 9, ! “ & ’ ( ) * + , - . / : ; ? = (espace).  
  
 Le jeu de caractères étendus inclut les caractères dans les caractères de langue sélectionnée ensemble et des lettres minuscules, caractères de base et d’autres caractères spéciaux : a à z, % @ [] _ {} \ &#124; \< > ~ # $.  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie EDI](../core/edi-messaging.md)   
 [Schémas EDI](../core/edi-schemas.md)