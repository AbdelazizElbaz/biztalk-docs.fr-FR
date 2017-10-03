---
title: "Configuration de jeu de caractères de secours propriétés et des séparateurs (EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eadc9c1-ebec-42f5-a9ca-06cb28bebcdf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b517a98130f2d245d68083dc16c65865950800c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-charset-and-separator-properties-edifact"></a>Configuration des propriétés du jeu de caractères et des séparateurs de secours (EDIFACT)
Dans l'accord de secours, vous pouvez spécifier le jeu de caractères (UNA) que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour valider les propriétés de tiers lors de la création de l'enveloppe pour un message EDIFACT sortant. Vous pouvez également spécifier les séparateurs et terminateurs (UNB) utilisés pour les segments dans l'échange.  
  
 Dans le segment UNA, vous définissez la méthode utilisée par BizTalk Server pour générer le segment UNA d'un échange EDIFACT envoyé au tiers. Le segment UNA définit les caractères qui seront utilisés comme séparateurs et indicateurs pour un échange EDIFACT. Utilisez ce segment uniquement si l'échange contient des caractères de séparation non standard.  
  
 Dans le segment UNB, vous définissez le jeu de caractères EDIFACT à utiliser.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-character-set-and-separators"></a>Pour configurer le jeu de caractères et les séparateurs  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **jeu de caractères et Séparateurs**.  
  
3.  Dans le **syntaxe (UNB1)** section, procédez comme suit :  
  
    1.  Pour **identificateur (UNB1.1)**, entrez le jeu de caractères EDIFACT à appliquer à l’échange sortant. Ce champ est obligatoire.  
  
    2.  Pour **Version (UNB1.2)**, sélectionnez une valeur comprise entre **1** et **4**. Il s’agit d’un champ facultatif.  
  
4.  Dans le **séparateurs** section, procédez comme suit :  
  
    1.  Pour **séparateur d’éléments de données composites (UNA1)**, entrez une valeur pour le séparateur d’éléments de données composites qui sépare les éléments de données simples au sein d’éléments de données composites. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré est modifié automatiquement si vous modifiez son format.  
  
    2.  Pour **séparateur d’éléments de données (UNA2)**, entrez une valeur pour le séparateur d’éléments de données qui sépare les éléments de données composites consistant en deux ou plusieurs éléments de données simples ou des éléments de données simples qui ne font pas partie d’un composite. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré est modifié automatiquement si vous modifiez son format.  
  
    3.  Pour **notation décimale (UNA3)**, sélectionnez la notation décimale à utiliser dans l’échange sortant.  
  
    4.  Pour **l’indicateur de version (UNA4)**, entrez une valeur pour l’indicateur de version qui indique que le caractère suivant n’est pas un séparateur de syntaxe, une marque de fin ou un caractère d’échappement, mais fait partie des données d’origine. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré est modifié automatiquement si vous modifiez son format.  
  
    5.  Pour **séparateur de répétition (UNA5)**, entrez une valeur pour le séparateur de répétition utilisé pour séparer les segments qui se répètent dans un jeu de transactions. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré est modifié automatiquement si vous modifiez son format.  
  
    6.  Pour **terminateur de Segment (UNA6)**, entrez une valeur pour le terminateur de segment qui indique la fin d’un segment EDI.  
  
    7.  Pour **suffixe UNA6**, sélectionnez le caractère que BizTalk Server utilisera avec l’identificateur de Segment : **aucun**, **CR** (retour chariot), **LF** (saut de ligne) ou **CR LF** (retour chariot/ligne de flux). Si vous désignez un suffixe, l'élément de données du terminateur de segment peut être vide. Si le terminateur de segment n'est pas indiqué, vous devez désigner un suffixe. La combinaison terminateur de segment-suffixe peut être l'une des suivantes :  
  
        -   Terminateur de segment  
  
        -   Terminateur de segment + retour chariot  
  
        -   Terminateur de segment + retour chariot/saut de ligne  
  
        -   Retour chariot  
  
        -   saut de ligne  
  
        -   Retour chariot/saut de ligne  
  
5.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider et accepter les modifications et fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)