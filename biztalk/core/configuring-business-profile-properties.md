---
title: Configuration des propriétés de profil d’entreprise | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.businessprofile.properties
ms.assetid: d3c87777-9bcd-4482-bbb7-efea08cdeead
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b43f6af9999b0c09698d6cebe6fbe9af505a42a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-business-profile-properties"></a>Configuration des propriétés de profil d'entreprise
Un profil d'entreprise représente un département dans une organisation. Tout comme une organisation peut inclure plusieurs départements (comptabilité, achat, expédition, etc.), un tiers peut inclure plusieurs profils d'entreprise représentant chacun un département d'une organisation. Les propriétés d'un profil d'entreprise contiennent les informations suivantes :  
  
-   informations générales telles que le nom du profil d'entreprise ;  
  
-   identités uniques qui peuvent être associées à un profil d'entreprise ;  
  
-   paramètres de codage (pour les messages X12 et EDIFACT) et paramètres de protocole (AS2) qui définissent l'envoi de messages et la réception de messages d'un autre tiers par le profil d'entreprise.  
  
 Pour plus d’informations sur les profils d’entreprise, consultez [profils d’entreprise](http://msdn.microsoft.com/library/f8286130-57fe-40ed-9fd8-81da2c8baaaf). Pour plus d’informations sur les paramètres de protocole de codage et de transport, consultez [paramètres de protocole](../core/protocol-settings.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-business-profile-properties"></a>Pour configurer des propriétés de profil d'entreprise  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **Parties** nœud. Dans le **tiers et profils d’entreprise** volet, avec le bouton droit à un tiers, pointez sur Nouveau, puis cliquez sur **profil d’entreprise**.  
  
2.  Dans le **général** sous l’onglet dans le **général** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Entrez un nom de profil d'entreprise.|  
    |**Description**|Entrez la description du profil d'entreprise.|  
    |**Propriétés supplémentaires – nom / valeur**|Entrez une paire nom-valeur pour mémoriser toute information sur le tiers. Vous pouvez ajouter autant de paires nom-valeur que vous voulez. **Remarque :** les paires nom-valeur ne sont pas utilisés par BizTalk Server pour tout traitement, ces données sont à titre d’information uniquement.|  
    |**Delete**|Cliquez pour supprimer la paire nom-valeur sélectionnée.|  
  
3.  Le cas échéant, ajoutez des identités d'entreprise pour les profils d'entreprise. Dans le **général** sous l’onglet dans le **identités** page, procédez comme suit :  
  
    > [!NOTE]
    >  L'ajout d'identités d'entreprise à ce stade n'est pas obligatoire. Vous pouvez ajouter les identités d'entreprise ultérieurement, dans le cadre d'un accord pour le profil d'entreprise. Si vous choisissez d'ajouter les identités d'entreprise maintenant, celles-ci seront disponibles lors de la création d'un accord pour ce profil d'entreprise.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Cliquez sur la cellule vide, puis dans la grille déroulante, sélectionnez un corps d'authentification qui fournit des identités d'entreprise uniques aux organisations. Par exemple, **D-U-N-S (DUN and Bradstreet)**. Deux partenaires commerciaux peuvent opter pour une identité d'entreprise dont ils conviennent mutuellement. Dans ce cas, sélectionnez **défini mutuellement** (pour EDIFACT) ou **défini mutuellement (X12)** (pour X12).|  
    |**Qualificateur**|Affiche une valeur prédéfinie basée sur la valeur que vous avez sélectionné pour **nom**.|  
    |**Valeur**|Entrez une valeur pour l'identité d'entreprise. Vous devez prendre en compte les points suivants lorsque vous définissez une valeur pour les identités d'entreprise :<br /><br /> -Pour un tiers donné, vous pouvez avoir plusieurs profils d’entreprise à l’aide de la même combinaison de nom de l’identité et la valeur d’identité. Par exemple, vous pouvez avoir deux profils d’entreprise pour un tiers avec **nom** en tant que **défini mutuellement (X12)** et **valeur** en tant que **THEM**.<br />-Entre plusieurs tiers, vous ne pouvez avoir deux profils d’entreprise à l’aide de la même combinaison de nom de l’identité et la valeur d’identité.|  
    |**Delete**|Cliquez pour supprimer l'identité sélectionnée.|  
  
4.  Le cas échéant, ajoutez les paramètres de protocole pour les messages X12.  
  
    1.  Dans le **propriétés de profil** boîte de dialogue, à partir de l’angle supérieur droit, cliquez sur **ajouter des paramètres de protocole**, pointez sur **paramètres de codage**, puis cliquez sur **X12** .  
  
    2.  Un nouvel onglet est ajouté à côté du **général** onglet.  Sur le **commune** page de récemment ajouté sous l’onglet du **nom des paramètres de protocole** texte, entrez un nom pour identifier cet ensemble de paramètres de protocole de codage. Le nom de l'onglet a également la valeur que vous spécifiez dans la zone de texte.  
  
    3.  Vous pouvez définir les propriétés de X12 dans le cadre d'un profil d'entreprise ou directement dans l'accord. Si vous définissez les propriétés dans le cadre du profil d'entreprise, les mêmes paramètres sont disponibles lorsque vous créez un accord. Etant donné que les mêmes propriétés peuvent être définies au niveau de deux emplacements, ce document fournit des instructions sur la manière de définir les propriétés uniquement dans le cadre de l'accord. Si vous voulez définir les propriétés dans le cadre du profil d'entreprise, le tableau ci-dessous fournit des liens vers les sections appropriées qui contiennent des informations sur la définition des propriétés.  
  
        > [!NOTE]
        >  Les paramètres entrants s'appliquent à tous les messages reçus par un tiers. Les paramètres sortants s'appliquent à tous les messages envoyés par un tiers.  
  
        > [!NOTE]
        >  Même si vous spécifiez les paramètres de protocole dans le cadre du profil d'entreprise, vous pouvez toujours remplacer les paramètres pour un accord spécifique.  
  
        |Paramètre|Description disponible à|  
        |-------------|------------------------------|  
        |**Trafic entrant de paramètres > Paramètres d’échange > Validation**|[Configuration de la Validation (paramètres d’échange X12)](../core/configuring-validation-x12-interchange-settings.md)|  
        |**Trafic entrant de paramètres > Paramètres d’échange > Paramètres de l’hôte Local**|[Configuration des paramètres de l’hôte Local (paramètres d’échange X12)](../core/configuring-local-host-settings-x12-interchange-settings.md) (paramètres du récepteur)|  
        |**Trafic entrant de paramètres > Paramètres du jeu de transactions > liste du jeu de transactions**|[Configuration de la liste (X12) informatisés](../core/configuring-transaction-set-list-x12.md)|  
        |**Trafic entrant de paramètres > Paramètres du jeu de transactions > Validation**|[Configuration de la Validation (paramètres de Transaction de X12)](../core/configuring-validation-x12-transaction-set-settings.md)|  
        |**Paramètres entrante > du document informatisé Paramètres > Paramètres de l’hôte Local**|[Configuration des paramètres de l’hôte Local (X12-paramètres)](../core/configuring-local-host-settings-x12-transaction-set-settings.md)|  
        |**Les paramètres sortants > Paramètres d’échange > identificateurs supplémentaires**|[Configuration des identificateurs (X12)](../core/configuring-identifiers-x12.md)|  
        |**Les paramètres sortants > Paramètres d’échange > accusés de réception**|[Configuration des accusés de réception (X12)](../core/configuring-acknowledgements-x12.md)|  
        |**Les paramètres sortants > Paramètres d’échange > enveloppes**|[Configuration d’enveloppes (paramètres d’échange X12)](../core/configuring-envelopes-x12-interchange-settings.md)|  
        |**Les paramètres sortants > Paramètres d’échange > jeu de caractères et séparateurs**|[Configuration de jeu de caractères et séparateurs (X12)](../core/configuring-charset-and-separators-x12.md)|  
        |**Les paramètres sortants > Paramètres d’échange > numéros de contrôle**|[Configuration des paramètres de l’hôte Local (paramètres d’échange X12)](../core/configuring-local-host-settings-x12-interchange-settings.md) (paramètres de l’expéditeur)|  
        |**Les paramètres sortants > Paramètres du jeu de transactions > enveloppes**|[Configuration d’enveloppes (paramètres de Transaction de X12)](../core/configuring-envelopes-x12-transaction-set-settings.md)|  
  
        > [!NOTE]
        >  Vous pouvez avoir plus d'un ensemble de paramètres de protocole de codage X12 défini pour un profil d'entreprise.  
  
5.  Le cas échéant, ajoutez les paramètres de protocole pour les messages EDIFACT.  
  
    1.  Dans le **propriétés de profil** boîte de dialogue, à partir de l’angle supérieur droit, cliquez sur **ajouter des paramètres de protocole**, pointez sur **paramètres de codage**, puis cliquez sur  **EDIFACT**.  
  
    2.  Un nouvel onglet est ajouté à côté du **général** onglet.  Sur le **commune** page de récemment ajouté sous l’onglet du **nom des paramètres de protocole** texte, entrez un nom pour identifier cet ensemble de paramètres de protocole de codage. Le nom de l'onglet a également la valeur que vous spécifiez dans la zone de texte.  
  
    3.  Vous pouvez définir les propriétés EDIFACT dans le cadre d'un profil d'entreprise ou directement dans l'accord. Si vous définissez les propriétés dans le cadre du profil d'entreprise, les mêmes paramètres sont disponibles lorsque vous créez un accord. Etant donné que les mêmes propriétés peuvent être définies au niveau de deux emplacements, ce document fournit des instructions sur la manière de définir les propriétés uniquement dans le cadre de l'accord. Si vous voulez définir les propriétés dans le cadre du profil d'entreprise, le tableau ci-dessous fournit des liens vers les sections appropriées qui contiennent des informations sur la définition des propriétés.  
  
        > [!NOTE]
        >  Les paramètres entrants s'appliquent à tous les messages reçus par un tiers. Les paramètres sortants s'appliquent à tous les messages envoyés par un tiers.  
  
        > [!NOTE]
        >  Même si vous spécifiez les paramètres de protocole dans le cadre du profil d'entreprise, vous pouvez toujours remplacer les paramètres pour un accord spécifique.  
  
        |Paramètre|Description disponible à|  
        |-------------|------------------------------|  
        |**Trafic entrant de paramètres > Paramètres d’échange > identificateurs supplémentaires**|[Configuration des identificateurs (EDIFACT)](../core/configuring-identifiers-edifact.md)|  
        |**Trafic entrant de paramètres > Paramètres d’échange > Validation**|[Configuration de la Validation (paramètres d’échange EDIFACT)](../core/configuring-validation-edifact-interchange-settings.md)|  
        |**Trafic entrant de paramètres > Paramètres d’échange > Paramètres de l’hôte Local**|[Configuration des paramètres de l’hôte Local (paramètres d’échange EDIFACT)](../core/configuring-local-host-settings-edifact-interchange-settings.md) (paramètres du récepteur)|  
        |**Trafic entrant de paramètres > Paramètres du jeu de transactions > liste du jeu de transactions**|[Configuration des documents informatisés liste (EDIFACT)](../core/configuring-transaction-set-list-edifact.md)|  
        |**Trafic entrant de paramètres > Paramètres du jeu de transactions > Validation**|[Configuration de la Validation (EDIFACT-informatisés paramètres)](../core/configuring-validation-edifact-transaction-set-settings.md)|  
        |**Paramètres entrante > du document informatisé Paramètres > Paramètres de l’hôte Local**|[Configuration des paramètres de l’hôte Local (EDIFACT-informatisés paramètres)](../core/configuring-local-host-settings-edifact-transaction-set-settings.md)|  
        |**Les paramètres sortants > Paramètres d’échange > identificateurs supplémentaires**|[Configuration des identificateurs (EDIFACT)](../core/configuring-identifiers-edifact.md)|  
        |**Les paramètres sortants > Paramètres d’échange > accusés de réception**|[Configuration des accusés de réception (EDIFACT)](../core/configuring-acknowledgements-edifact.md)|  
        |**Les paramètres sortants > Paramètres d’échange > enveloppes**|[Configuration d’enveloppes (paramètres d’échange EDIFACT)](../core/configuring-envelopes-edifact-interchange-settings.md)|  
        |**Les paramètres sortants > Paramètres d’échange > jeu de caractères et séparateurs**|[Configuration de jeu de caractères et séparateurs (EDIFACT)](../core/configuring-charset-and-separators-edifact.md)|  
        |**Les paramètres sortants > Paramètres d’échange > numéros de contrôle**|[Configuration des paramètres de l’hôte Local (paramètres d’échange EDIFACT)](../core/configuring-local-host-settings-edifact-interchange-settings.md) (paramètres de l’expéditeur)|  
        |**Les paramètres sortants > Paramètres du jeu de transactions > enveloppes**|[Configuration d’enveloppes (EDIFACT-informatisés paramètres)](../core/configuring-envelopes-edifact-transaction-set-settings.md)|  
  
        > [!NOTE]
        >  Vous pouvez avoir plus d'un ensemble de paramètres de protocole de codage EDIFACT défini pour un profil d'entreprise.  
  
6.  Le cas échéant, ajoutez les paramètres de protocole pour le transport AS2.  
  
    1.  Dans le **propriétés de profil** boîte de dialogue, à partir de l’angle supérieur droit, cliquez sur **ajouter des paramètres de protocole**, pointez sur **paramètres de Transport**, puis cliquez sur **AS2** .  
  
    2.  Un nouvel onglet est ajouté à côté du **général** onglet.  Sur le **commune** page de récemment ajouté sous l’onglet du **nom des paramètres de protocole** texte, entrez un nom pour identifier cet ensemble de paramètres de protocole de transport. Le nom de l'onglet a également la valeur que vous spécifiez dans la zone de texte.  
  
    3.  Vous pouvez définir les propriétés AS2 dans le cadre d'un profil d'entreprise ou directement dans l'accord. Si vous définissez les propriétés dans le cadre du profil d'entreprise, les mêmes paramètres sont disponibles lorsque vous créez un accord. Etant donné que les mêmes propriétés peuvent être définies au niveau de deux emplacements, ce document fournit des instructions sur la manière de définir les propriétés uniquement dans le cadre de l'accord. Si vous voulez définir les propriétés dans le cadre du profil d'entreprise, le tableau ci-dessous fournit des liens vers les sections appropriées qui contiennent des informations sur la définition des propriétés.  
  
        > [!NOTE]
        >  Les paramètres entrants s'appliquent à tous les messages reçus par un tiers. Les paramètres sortants s'appliquent à tous les messages envoyés par un tiers.  
  
        > [!NOTE]
        >  Même si vous spécifiez les paramètres de protocole dans le cadre du profil d'entreprise, vous pouvez toujours remplacer les paramètres pour un accord spécifique.  
  
        |Paramètre|Description disponible à|  
        |-------------|------------------------------|  
        |**Paramètres entrante > Validation**|[Validation de la configuration (AS2)](../core/configuring-validation-as2.md)|  
        |**Trafic entrant de paramètres > Paramètres de l’hôte Local > Paramètres HTTP des Messages**|[Configuration des paramètres HTTP des Messages](../core/configuring-http-settings-for-messages.md)|  
        |**Trafic entrant de paramètres > Paramètres de l’hôte Local > généré paramètres MDN**|[Configuration des paramètres MDN du récepteur](../core/configuring-receiver-mdn-settings.md)|  
        |**Trafic entrant de paramètres > Paramètres de l’hôte Local > Message de suivi (NRR)**|[Configuration des messages du récepteur (NRR) de suivi](../core/configuring-receiver-message-tracking-nrr.md)|  
        |**Les paramètres sortants > accusés de réception (MDN)**|[Configuration des accusés de réception (MDN) (AS2)](../core/configuring-acknowledgements-mdns-as2.md)|  
        |**Les paramètres sortants > Paramètres de l’hôte Local > Général**|[Configuration des paramètres généraux de l’hôte Local (AS2)](../core/configuring-general-local-host-settings-as2.md)|  
        |**Les paramètres sortants > Paramètres de l’hôte Local > Paramètres HTTP des MDN**|[Configuration des paramètres HTTP des MDN](../core/configuring-http-settings-for-mdns.md)|  
        |**Les paramètres sortants > Paramètres de l’hôte Local > Message de suivi (NRR)**|[Configuration des messages de l’expéditeur (NRR) de suivi](../core/configuring-sender-message-tracking-nrr.md)|  
        |**Les paramètres sortants > le certificat de Signature**|[Configuration des certificats de Signature (AS2)](../core/configuring-signature-certificates-as2.md)|  
  
        > [!NOTE]
        >  Vous pouvez avoir plus d'un ensemble de paramètres de protocole de transfert AS2 défini pour un profil d'entreprise.  
  
7.  Cliquez sur **appliquer** pour accepter les propriétés, ou cliquez sur **OK** pour terminer la configuration. Les deux actions valident les paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)