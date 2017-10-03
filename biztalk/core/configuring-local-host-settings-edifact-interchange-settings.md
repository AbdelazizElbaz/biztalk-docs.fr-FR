---
title: "Configuration des paramètres de l’hôte Local (paramètres d’échange EDIFACT) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1cf8696-d1f4-49aa-aa0a-ecf66f55e01d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b93833e8143f1b6706d86295e3f5db8292bc6c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-local-host-settings-edifact-interchange-settings"></a>Configuration des paramètres de l'hôte local (EDIFACT - Paramètres d'échange)
Les paramètres de l'hôte local déterminent la façon dont les échanges EDI sont traités. Les paramètres de cette page peuvent être répartis en deux catégories – les paramètres du récepteur (pour les échanges entrants) et les paramètres de l'expéditeur (pour les échanges sortants). Dans les paramètres du récepteur, vous pouvez spécifier si un lot entrant sera divisé en documents informatisés ou conservés. S'il est conservé, vous pouvez spécifier si BizTalk Server doit suspendre l'échange ou le document informatisé si une erreur se produit. Dans les paramètres de l'expéditeur, vous pouvez spécifier comment les numéros de contrôle sont générés pour les messages sortants.  
  
> [!IMPORTANT]
>  Les propriétés suivantes sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers**case à cocher pour tiers A.  
>   
>  -   Toutes les propriétés dans le **paramètres de l’expéditeur** section.  
>   
>  De même, les propriétés suivantes sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.  
>   
>  -   Toutes les propriétés dans le **paramètres du récepteur** section.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-local-host--receivers-settings"></a>Pour configurer l'hôte local – paramètres du récepteur  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **paramètres d’hôte Local**.  
  
3.  Dans le **EDIFACT ACK** section, pour désigner les numéros de référence de jeu de transaction à utiliser dans un accusé de réception, entrez une valeur pour le préfixe, une plage de numéros de référence et le suffixe.  
  
     Cliquez sur **réinitialiser** pour réinitialiser le document informatisé numéro de référence à la limite inférieure. Sélectionnez **réinitialiser à la limite inférieure lorsque la limite** avoir [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] réinitialiser le numéro de référence sur la limite de valeur de plage inférieure si la limite maximale est dépassée.  
  
4.  Désactivez le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** pour renvoyer l’accusé de réception via un distinct port d’envoi. Conservez la sélection pour renvoyer l'accusé de réception sur le port d'envoi associé au port de réception de requête-réponse bidirectionnel.  
  
5.  Désactivez **masquer les informations de sécurité / d’autorisation/mot de passe** désactiver le masquage des informations de sécurité d’autorisation/de mot de passe (champs UNB6.1 et UNB6.2) dans la propriété de contexte pour empêcher la divulgation d’informations.  
  
    > [!NOTE]
    >  Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit des messages, il promeut l'en-tête UNB dans le contexte du message. Sans le masquage, les informations concernant la sécurité dans le contexte seraient accessibles à tout individu disposant de privilèges d'administrateur. Pour masquer ces informations, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] remplace chaque caractère des informations avec un  **#**  caractère. Il s’agit d’un processus à sens unique : le  **#**  caractères ne peuvent pas être convertis en caractères réels.  
  
6.  Dans le **entrants option de traitement par lots** liste déroulante, procédez comme suit :  
  
    1.  Sélectionnez l’option par défaut **fractionner l’échange en documents informatisés - suspendre les documents informatisés en cas d’erreur** pour indiquer que BizTalk Server doit analyser chaque document informatisé d’un échange en un document XML distinct. BizTalk Server applique alors l'enveloppe appropriée au document informatisé et l'achemine vers la base de données MessageBox. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt uniquement ces documents informatisés.  
  
    2.  Sélectionnez **fractionner l’échange en documents informatisés - suspendre l’échange en cas d’erreur** pour indiquer que BizTalk Server doit analyser chaque document informatisé d’un échange en un document XML distinct. BizTalk Server applique alors l'enveloppe appropriée au document informatisé et l'achemine vers la base de données MessageBox. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt l'ensemble de l'échange.  
  
    3.  Sélectionnez **préserver l’échange : suspendre l’échange en cas d’erreur** pour spécifier que BizTalk Server doit laisser l’échange intact, créant ainsi un document XML pour l’ensemble de l’échange par lot. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt l'ensemble de l'échange.  
  
    4.  Sélectionnez **préserver l’échange : suspendre les documents informatisés en cas d’erreur** pour spécifier que BizTalk Server doit laisser l’échange intact, créant ainsi un document XML pour l’ensemble de l’échange par lot. Avec cette option, si un ou plusieurs documents informatisés dans l’échange la validation échouent, BizTalk Server interrompt uniquement ces documents informatisés, tout en continuant à traiter tous les autres documents informatisés.  
  
        > [!NOTE]
        >  Si vous sélectionnez **préserver l’échange : suspendre l’échange en cas d’erreur** ou **préserver l’échange : suspendre les documents informatisés en cas d’erreur**, les paramètres de propriété sur le **définition des segments ISA**  et **définition GS et ST Segment** pages (qui déterminent la façon dont BizTalk Server crée les en-têtes ISA, GS et ST d’un échange sortant) ne s’appliquent pas. Les en-têtes de l'échange, du groupe et du document informatisé qui existent dans l'échange conservé sont préservés lorsque le pipeline d'envoi traite ce dernier à des fins d'envoi.  
  
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
 [Configuration des paramètres d’échange (EDIFACT)](../core/configuring-interchange-settings-edifact.md)