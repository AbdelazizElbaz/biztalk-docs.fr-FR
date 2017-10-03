---
title: "Configuration des paramètres de secours de l’hôte Local (paramètres d’échange EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eecf5abb-9c12-44b0-bc58-94cb138515c3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dc98c62870632501c5b5330ed72ad5aee971fdd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-local-host-settings-edifact-interchange-settings"></a>Configuration des paramètres de secours de l'hôte local (EDIFACT - Paramètres d'échange)
Les paramètres de l'hôte local déterminent la façon dont les échanges EDI sont traités. Les paramètres de cette page peuvent être répartis en deux catégories – les paramètres du récepteur (pour les échanges entrants) et les paramètres de l'expéditeur (pour les échanges sortants). Dans les paramètres du récepteur, vous pouvez spécifier comment le numéro de contrôle de l'accusé de réception sera généré. Dans les paramètres de l'expéditeur, vous pouvez spécifier comment les numéros de contrôle sont générés pour les messages sortants.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-local-host--receivers-settings"></a>Pour configurer l'hôte local – paramètres du récepteur  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **paramètres de secours EDIFACT**.  
  
2.  Dans le **paramètres de secours EDIFACT** boîte de dialogue le **accords EDIFACT** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **hôte Local Paramètres**.  
  
3.  Dans le **EDIFACT ACK** section, pour désigner les numéros de référence de jeu de transaction à utiliser dans un accusé de réception, entrez une valeur pour le préfixe, une plage de numéros de référence et le suffixe.  
  
     Cliquez sur **réinitialiser** pour réinitialiser le document informatisé numéro de référence à la limite inférieure. Sélectionnez **réinitialiser à la limite inférieure lorsque la limite** avoir [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] réinitialiser le numéro de référence sur la limite de valeur de plage inférieure si la limite maximale est dépassée.  
  
### <a name="to-configure-local-host--senders-settings"></a>Pour configurer l'hôte local – paramètres de l'expéditeur  
  
1.  Pour **numéro de contrôle d’échange (UNB5)**, entrez une plage de valeurs pour le numéro de contrôle être utilisé par BizTalk Server lors de la génération d’un échange sortant. Entrez une valeur numérique située entre 1 et 999999999. Il s’agit d’un champ obligatoire.  
  
    > [!NOTE]
    >  Le premier champ (**UNB5.1**) est les préfixe ; les deuxième et le troisième champs (**UNB5.2**) incluent la plage de numéros à utiliser comme le numéro de contrôle ; et le quatrième champ (**UNB5.3**) est le suffixe. Le préfixe et le suffixe sont facultatifs. Le numéro de contrôle, lui, est obligatoire. Le numéro de contrôle est incrémenté pour chaque nouveau message. Le préfixe et le suffixe restent identiques. Le numéro de contrôle peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13. Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
    >   
    >  Pour réinitialiser le numéro de contrôle à la valeur minimale spécifiée, cliquez sur le **réinitialiser** bouton. Vérifiez **réinitialiser à la limite inférieure lorsque la limite** pour rétablir automatiquement à la valeur minimale si la valeur maximale est dépassée.  
  
2.  Pour **numéro de contrôle de groupe (UNG5)**, entrez le préfixe, plage de numéros et le suffixe que BizTalk Server doit utiliser pour le numéro de contrôle de groupe du premier échange qu’il envoie de référence.  
  
    > [!NOTE]
    >  Le premier champ (**UNG5.1**) est les préfixe ; les deuxième et le troisième champs (**UNG5.2**) incluent la plage de numéros à utiliser pour le numéro de contrôle de groupe ; et le quatrième champ (**UNG5.3**) correspond au suffixe. Le préfixe et le suffixe sont facultatifs. Le numéro de contrôle, lui, est obligatoire. Le numéro de contrôle est incrémenté pour chaque nouveau message, jusqu'à atteindre la valeur maximale. Le préfixe et le suffixe restent identiques. Seuls les chiffres sont autorisés dans **UNG5.2**. Le numéro de contrôle peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13. Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
    >   
    >  Pour réinitialiser le numéro de contrôle de groupe pour la valeur minimale spécifiée, cliquez sur le **réinitialiser** bouton. Vérifiez **réinitialiser à la limite inférieure lorsque la limite** pour rétablir automatiquement à la valeur minimale si la valeur maximale est dépassée.  
  
3.  Pour **en-tête de Message (UNH)**, cliquez sur **appliquer le nouvel ID**, entrez le préfixe, la plage de numéros de référence et entrez le suffixe que BizTalk Server doit utiliser pour le numéro de référence de jeu de transactions.  
  
    > [!NOTE]
    >  Le premier champ (**UNH1.1**) est les préfixe ; les deuxième et le troisième champs (**UNH1.2**) sont la plage de numéros de référence ; et le quatrième champ (**UNH1.3**) correspond au suffixe. Le préfixe et le suffixe sont facultatifs. Le numéro de référence, lui, est obligatoire. Le numéro de référence est incrémenté pour chaque nouveau message. Le préfixe et le suffixe restent identiques. La plage de valeurs par défaut du numéro de référence est comprise entre 1 et 99999999999999. Seuls les chiffres sont autorisés dans **UNH1.2**. Le numéro de contrôle peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13. Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
    >   
    >  Pour réinitialiser le document informatisé numéro de contrôle à la valeur minimale, cliquez sur **réinitialiser**. Sélectionnez **réinitialiser à la limite inférieure lorsque la limite** pour réinitialiser le numéro de contrôle à la valeur minimale si la valeur maximale a été dépassée.  
  
4.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés de l’accord de secours EDIFACT pour le traitement des échanges](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)