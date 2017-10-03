---
title: "Configuration de jeu de caractères de secours et les propriétés d’un séparateur (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 477f4952-6a4e-4e98-a37f-f6e1fe7db3d3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 633ea22c611eb0fab994fd62250b9cb9ff8a0f2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-charset-and-separator-properties-x12"></a>Configuration des propriétés du jeu de caractères et des séparateurs de secours (X12)
Dans l'accord de secours, vous pouvez spécifier le jeu de caractères que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise pour valider les propriétés de tiers lors de la création de l'enveloppe pour un message X12 sortant. Vous pouvez également spécifier les séparateurs et terminateurs utilisés pour les segments dans l'échange.  
  
> [!NOTE]
>  Les paramètres décrits dans cette rubrique s'appliquent également aux échanges HIPAA.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-character-set-and-separators"></a>Pour configurer le jeu de caractères et les séparateurs  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.  
  
2.  Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **jeu de caractères et séparateurs** .  
  
3.  À partir de la **du jeu de caractères à utiliser** liste déroulante, sélectionnez le X12 jeu de caractères à être utilisé pour valider les propriétés que vous entrez pour l’accord.  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise uniquement ce paramètre pour valider les valeurs entrées pour les propriétés de l'accord correspondant. Le pipeline d'envoi ou de réception ignore cette propriété de jeu de caractères lors de l'exécution du traitement.  
  
4.  Pour **élément de données**, entrez un seul caractère que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour séparer les éléments de données composites consistant en deux ou plusieurs éléments de données simples et des éléments de données simples qui ne font pas partie d’un élément composite. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.  
  
5.  Pour **séparateur d’éléments composites (ISA16)**, entrez un seul caractère que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour séparer les éléments de données simples au sein d’éléments de données composites. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.  
  
6.  Pour **terminateur de Segment**, entrez un seul caractère que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour indiquer la fin d’un segment EDI. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.  
  
7.  Pour **suffixe**, sélectionnez le caractère qui [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera avec l’identificateur de Segment : **aucun**, **CR** (retour chariot), **LF** (saut de ligne) ou **CR LF** (retour chariot/ligne de flux). Si vous désignez un suffixe, l'élément de données du terminateur de segment peut être vide. Si le terminateur de segment n'est pas indiqué, vous devez désigner un suffixe. La combinaison terminateur de segment-suffixe peut être l'une des suivantes :  
  
    -   Terminateur de segment  
  
    -   Terminateur de segment + retour chariot  
  
    -   Terminateur de segment + retour chariot/saut de ligne  
  
    -   Retour chariot  
  
    -   saut de ligne  
  
    -   Retour chariot/saut de ligne  
  
8.  Si les données de charge contient des caractères qui sont également utilisés comme séparateurs de données, segment ou composant, vérifiez **remplacer les séparateurs dans la charge utile avec** et spécifiez un caractère de remplacement. Lors de la création du message X12 sortant, les instances des caractères de séparation dans les données de charge sont remplacées par le caractère spécifié. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.  
  
9. Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration X12 propriétés d’accord de secours pour le traitement de l’échange](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)