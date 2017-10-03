---
title: "Configuration de jeu de caractères et séparateurs (X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6249f2e1-70b0-4960-bbc4-0c3fefd26faa
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43e32c4d9a240c3302126fc403d64efd787ed54c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-charset-and-separators-x12"></a>Configuration du jeu de caractères et des séparateurs (X12)
Dans l'accord de partenariat, vous pouvez spécifier le jeu de caractères utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour valider les propriétés de tiers lors de la création de l'enveloppe pour un message X12 sortant. Vous pouvez également spécifier les séparateurs et terminateurs utilisés pour les segments dans l'échange.  
  
> [!NOTE]
>  Les paramètres décrits dans cette rubrique s'appliquent également aux échanges HIPAA.  
  
> [!IMPORTANT]
>  Les propriétés suivantes sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
>   
>  -   **Élément de données**  
> -   **Séparateur d’éléments composites (ISA16)**  
> -   **Terminateur de segment**  
> -   **Suffixe**  
> -   **Remplacer les séparateurs dans la charge par**  
>   
>  Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers. Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-character-set-and-separators"></a>Pour configurer le jeu de caractères et les séparateurs  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **jeu de caractères et séparateurs**.  
  
3.  À partir de la **du jeu de caractères à utiliser** liste déroulante, sélectionnez le X12 jeu de caractères à être utilisé pour valider les propriétés que vous entrez pour l’accord.  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise uniquement ce paramètre pour valider les valeurs entrées pour les propriétés de l'accord correspondant. Le pipeline d'envoi ou de réception ignore cette propriété de jeu de caractères lors de l'exécution du traitement.  
  
4.  Pour **élément de données**, entrez un seul caractère que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour séparer les éléments de données composites consistant en deux ou plusieurs éléments de données simples et des éléments de données simples qui ne font pas partie d’un élément composite. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.  
  
5.  Pour **séparateur d’éléments composites (ISA16)**, entrez un seul caractère que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour séparer les éléments de données simples au sein d’éléments de données composites. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.  
  
6.  Pour **terminateur de Segment**, entrez un caractère unique pour indiquer la fin d’un segment EDI. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales.  
  
     Si le type est **Char**, la valeur par défaut est  **~** .  
  
     Si le type est **Hex**, la valeur par défaut est **7E**.  
  
     Cet élément de données est requis.  
  
     Cet élément est limité aux valeurs du jeu de caractères ASCII. Cette propriété n'est pas validée par rapport au jeu de caractères X12 défini dans la page Général.  
  
     Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.  
  
7.  Pour **suffixe**, sélectionnez le caractère à utiliser **avec** la valeur du terminateur de Segment. Les options sont les suivantes :  
  
    -   **Aucun**: par défaut  
  
    -   **CR**: retour chariot  
  
    -   **LF**: saut de ligne  
  
    -   **CR LF**: flux de retour de ligne de chariot  
  
     Les combinaisons d’un terminateur de segment et d’un suffixe sont les suivantes :  
  
    -   **N’importe quel** terminateur de Segment + **aucun** suffixe  
  
    -   **N’importe quel** terminateur de Segment + **CR** suffixe  
  
    -   **N’importe quel** terminateur de Segment + **CR LF** suffixe  
  
    -   **D (Hex)** terminateur de Segment + **aucun** suffixe : cette combinaison agit comme si le terminateur de Segment est vide et suffixe est définie sur CR.  
  
    -   Un terminateur de Segment (Hex) + **aucun** suffixe : cette combinaison agit comme si le terminateur de Segment est vide et suffixe est définie sur LF.  
  
    -   **D (Hex)** terminateur de Segment + **LF** suffixe : cette combinaison agit comme si le terminateur de Segment était CR et suffixe est défini sur LF.  
  
8.  Si les données de charge contient des caractères qui sont également utilisés comme séparateurs de données, segment ou composant, vérifiez **remplacer les séparateurs dans la charge utile avec** et spécifiez un caractère de remplacement. Lors de la création du message X12 sortant, les instances des caractères de séparation dans les données de charge sont remplacées par le caractère spécifié. Sélectionnez **Char** pour un élément de données caractère ou **Hex** pour un élément de données hexadécimales. Le caractère entré change automatiquement lorsque vous modifiez le format **Char** à **Hex** ou vice versa.  
  
9. Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (X12)](../core/configuring-interchange-settings-x12.md)