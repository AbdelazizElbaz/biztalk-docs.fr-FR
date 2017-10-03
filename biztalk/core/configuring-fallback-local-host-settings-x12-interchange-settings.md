---
title: "Configuration des paramètres de secours de l’hôte Local (paramètres d’échange X12) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b552fa2b-1154-491f-9bcf-aaba3b8f343f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a220f9c15c09cf667cf9b7b1805eba72634a17a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-local-host-settings-x12-interchange-settings"></a>Configuration des paramètres de secours de l'hôte local (X12 - Paramètres d'échange)
Les paramètres de l'hôte local déterminent la façon dont les échanges EDI sont traités. Les paramètres de cette page peuvent être répartis en deux catégories – les paramètres du récepteur (pour les échanges entrants) et les paramètres de l'expéditeur (pour les échanges sortants). Dans les paramètres du récepteur, vous pouvez spécifier comment le numéro de contrôle de l'accusé de réception ST02 sera généré. Dans les paramètres de l'expéditeur, vous pouvez spécifier comment les numéros de contrôle sont générés pour les messages sortants.  
  
> [!NOTE]
>  Les paramètres décrits dans cette rubrique s'appliquent également aux échanges HIPAA.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-local-host--receivers-settings"></a>Pour configurer l'hôte local – paramètres du récepteur  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Parties** nœud, puis cliquez sur **X12 paramètres de secours**.  
  
2.  Dans le **X12 paramètres de secours** boîte de dialogue le **X12 page accords** sous l’onglet sous la **paramètres de l’échange** , cliquez sur **paramètres d’hôte Local** .  
  
3.  Pour désigner la plage de numéros de contrôle de transaction utilisé dans un accusé de réception, entrez des valeurs dans le **numéro de contrôle de l’accusé de réception (ST02)** champs. Entrez une valeur numérique pour les deux champs du milieu et une valeur alphanumérique (si nécessaire) pour les champs préfixe et suffixe. Les champs du milieu sont obligatoires et contiennent les valeurs minimale et maximale du numéro de contrôle ; le préfixe et le suffixe sont facultatifs. La longueur maximale pour les trois champs est de neuf caractères.  
  
     Pour réinitialiser le document informatisé numéro de contrôle à la valeur minimale, cliquez sur **réinitialiser**. Vérifiez **réinitialiser à la limite inférieure lorsque la limite** pour réinitialiser le numéro de contrôle à la limite inférieure, une fois que la valeur maximale a été dépassée.  
  
### <a name="to-configure-local-host--senders-settings"></a>Pour configurer l'hôte local – paramètres de l'expéditeur  
  
1.  Pour **numéro de contrôle d’échange (ISA13)**, entrez une plage de valeurs pour le numéro de contrôle être utilisé par BizTalk Server lors de la génération d’un échange sortant. Entrez une valeur numérique située entre 1 et 999999999. Il s’agit d’un champ obligatoire.  
  
     Pour réinitialiser le numéro de contrôle à la valeur minimale spécifiée, cliquez sur le **réinitialiser** bouton. Vérifiez **réinitialiser à la limite inférieure lorsque la limite** pour rétablir automatiquement à la valeur minimale si la valeur maximale est dépassée.  
  
2.  Pour **numéro de contrôle de groupe (GS06)**, entrez la plage de numéros que BizTalk Server doit utiliser pour le numéro de contrôle de groupe. Entrez une valeur numérique comportant un caractère au minimum et neuf caractères au maximum. Ce champ est obligatoire.  
  
     Pour réinitialiser le numéro de contrôle de groupe pour la valeur minimale spécifiée, cliquez sur le **réinitialiser** bouton. Vérifiez **réinitialiser à la limite inférieure lorsque la limite** pour rétablir automatiquement à la valeur minimale si la valeur maximale est dépassée.  
  
3.  Pour **le numéro de contrôle de Transaction défini (ST02)**, cliquez sur **appliquer le nouvel ID**, puis entrez une plage de valeurs numériques pour les champs du milieu requis et des valeurs alphanumériques pour le préfixe et suffixe facultatifs. La longueur maximale pour les quatre champs est de neuf caractères.  
  
     Pour réinitialiser le document informatisé numéro de contrôle à la valeur minimale, cliquez sur **réinitialiser**. Sélectionnez **réinitialiser à la limite inférieure lorsque la limite** pour réinitialiser le numéro de contrôle à la valeur minimale si la valeur maximale a été dépassée.  
  
4.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration X12 propriétés d’accord de secours pour le traitement de l’échange](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)