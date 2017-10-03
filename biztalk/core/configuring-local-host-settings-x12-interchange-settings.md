---
title: "Configuration des paramètres de l’hôte Local (paramètres d’échange X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c66c1e63-c654-4ccb-b424-34c06f1ce94e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10172c700d8b3d8d2039e46f28d24ff39ba93aac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-local-host-settings-x12-interchange-settings"></a>Configuration des paramètres de l'hôte local (paramètres d'échange X12)
Les paramètres de l'hôte local déterminent la façon dont les échanges EDI sont traités. Les paramètres de cette page peuvent être répartis en deux catégories – les paramètres du récepteur (pour les échanges entrants) et les paramètres de l'expéditeur (pour les échanges sortants). Dans les paramètres du récepteur, vous pouvez spécifier si un lot entrant sera divisé en documents informatisés ou conservés. S'il est conservé, vous pouvez spécifier si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doit suspendre l'échange ou le document informatisé si une erreur se produit. Dans les paramètres de l'expéditeur, vous pouvez spécifier comment les numéros de contrôle sont générés pour les messages sortants  
  
> [!NOTE]
>  Les paramètres décrits dans cette rubrique s'appliquent également aux échanges HIPAA.  
  
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
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres de l’échange** , cliquez sur **paramètres d’hôte Local**.  
  
3.  Désactivez le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** pour renvoyer l’accusé de réception par un distinct port d’envoi. Conservez la sélection pour renvoyer l'accusé de réception sur le port d'envoi associé au port de réception de requête-réponse bidirectionnel.  
  
4.  Pour désigner la plage de numéros de contrôle de transaction utilisé dans un accusé de réception, entrez des valeurs dans le **numéro de contrôle de l’accusé de réception (ST02)** champs. Entrez une valeur numérique pour les deux champs du milieu et une valeur alphanumérique (si nécessaire) pour les champs préfixe et suffixe. Les champs du milieu sont obligatoires et contiennent les valeurs minimale et maximale du numéro de contrôle ; le préfixe et le suffixe sont facultatifs. La longueur maximale pour les trois champs est de neuf caractères.  
  
     Pour réinitialiser le document informatisé numéro de contrôle à la valeur minimale, cliquez sur **réinitialiser**. Vérifiez **réinitialiser à la limite inférieure lorsque la limite** pour réinitialiser le numéro de contrôle à la limite inférieure, une fois que la valeur maximale a été dépassée.  
  
5.  Sélectionnez **masquer les informations de sécurité / d’autorisation/mot de passe dans la propriété de contexte** case à cocher pour activer le masquage des informations de sécurité d’autorisation/de mot de passe (champs ISA2 et ISA4) dans la propriété de contexte pour empêcher des informations divulgation d’informations.  
  
    > [!NOTE]
    >  Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit des messages, il promeut l'en-tête ISA dans le contexte du message. Sans le masquage, les informations concernant la sécurité dans le contexte seraient accessibles à tout individu disposant de privilèges d'administrateur. Pour masquer ces informations, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] remplace chaque caractère des informations avec un  **#**  caractère. Il s’agit d’un processus à sens unique : le  **#**  caractères ne peuvent pas être convertis en caractères réels.  
  
6.  Dans le **entrants option de traitement par lots** liste déroulante, procédez comme suit :  
  
    1.  Sélectionnez l’option par défaut **fractionner l’échange en documents informatisés - suspendre les documents informatisés en cas d’erreur** pour indiquer que BizTalk Server doit analyser chaque document informatisé d’un échange en un document XML distinct. BizTalk Server applique alors l'enveloppe appropriée au document informatisé et l'achemine vers la base de données MessageBox. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt uniquement ces documents informatisés.  
  
    2.  Sélectionnez **fractionner l’échange en documents informatisés - suspendre l’échange en cas d’erreur** pour indiquer que BizTalk Server doit analyser chaque document informatisé d’un échange en un document XML distinct. BizTalk Server applique alors l'enveloppe appropriée au document informatisé et l'achemine vers la base de données MessageBox. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt l'ensemble de l'échange.  
  
    3.  Sélectionnez **préserver l’échange : suspendre l’échange en cas d’erreur** pour spécifier que BizTalk Server doit laisser l’échange intact, créant ainsi un document XML pour l’ensemble de l’échange par lot. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt l'ensemble de l'échange.  
  
    4.  Sélectionnez **préserver l’échange : suspendre les documents informatisés en cas d’erreur** pour spécifier que BizTalk Server doit laisser l’échange intact, créant ainsi un document XML pour l’ensemble de l’échange par lot. Lorsque cette option est sélectionnée et si la validation d'un ou plusieurs documents informatisés de l'échange échoue, BizTalk Server interrompt seulement ces documents informatisés et continue à traiter les autres.  
  
        > [!NOTE]
        >  Si vous sélectionnez **préserver l’échange : suspendre l’échange en cas d’erreur** ou **préserver l’échange : suspendre les documents informatisés en cas d’erreur**, l’échange, groupe et transaction définir les propriétés de segment (qui déterminent la façon dont BizTalk Server crée les en-têtes ISA, GS et ST d’un échange sortant) ne s’appliquent pas. Les en-têtes de l'échange, du groupe et du document informatisé qui existent dans l'échange conservé sont préservés lorsque le pipeline d'envoi traite ce dernier à des fins d'envoi.  
  
### <a name="to-configure-local-host--senders-settings"></a>Pour configurer l'hôte local – paramètres de l'expéditeur  
  
1.  Pour **numéro de contrôle d’échange (ISA13)**, entrez une plage de valeurs pour le numéro de contrôle être utilisé par BizTalk Server lors de la génération d’un échange sortant. Entrez une valeur numérique située entre 1 et 999999999. Il s’agit d’un champ obligatoire.  
  
     Pour réinitialiser le numéro de contrôle à la valeur minimale spécifiée, cliquez sur le **réinitialiser** bouton. Vérifiez **réinitialiser à la limite inférieure lorsque la limite** pour rétablir automatiquement à la valeur minimale si la valeur maximale est dépassée.  
  
2.  Pour **numéro de contrôle de groupe (GS06)**, entrez la plage de numéros que BizTalk Server doit utiliser pour le numéro de contrôle de groupe. Entrez une valeur numérique comportant un caractère au minimum et neuf caractères au maximum. Ce champ est obligatoire.  
  
     Pour réinitialiser le numéro de contrôle de groupe pour la valeur minimale spécifiée, cliquez sur le **réinitialiser** bouton. Vérifiez **réinitialiser à la limite inférieure lorsque la limite** pour rétablir automatiquement à la valeur minimale si la valeur maximale est dépassée.  
  
3.  Pour **le numéro de contrôle de Transaction défini (ST02)**, cliquez sur **appliquer le nouvel ID** , puis entrez une plage de valeurs numériques pour les champs du milieu requis et des valeurs alphanumériques pour le préfixe et suffixe facultatifs. La longueur maximale pour les quatre champs est de neuf caractères.  
  
     Pour réinitialiser le document informatisé numéro de contrôle à la valeur minimale, cliquez sur **réinitialiser**. Sélectionnez **réinitialiser à la limite inférieure lorsque la limite** pour réinitialiser le numéro de contrôle à la valeur minimale si la valeur maximale a été dépassée.  
  
4.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres d’échange (X12)](../core/configuring-interchange-settings-x12.md)