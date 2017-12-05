---
title: Comment configurer les Tickets SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO], configuring tickets
- SSO, tickets
- tickets [SSO], configuring
ms.assetid: 32f0384b-ac79-4cce-b3f5-f4f8a73a673a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3b19d14a35d42c4a46bf9527a97f5bf749b875f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-the-sso-tickets"></a>Comment configurer les Tickets d’authentification unique
Vous pouvez utiliser le composant logiciel enfichable MMC ou la ligne de commande pour contrôler entièrement le comportement de ticket du système d'authentification unique, y compris l'autorisation des tickets et leur validation par le système.  
  
 Vous pouvez utiliser Yes, No, On ou Off pour indiquer s’il faut autoriser ou de valider des tickets. Ces mots, dont la casse est indifférente, doivent être utilisés indépendamment de vos paramètres de langue.  
  
 Si la fonctionnalité Administration de l'authentification unique est installée sur un ordinateur distant, une opération IssueTicket peut être effectuée à distance. Notez que tout le trafic entre le module Administration de l'authentification unique et le module Moteur d'exécution (service ENTSSO) est chiffré.  
  
 L'utilitaire de ligne de commande ssomanage.exe permet de spécifier le délai d'expiration du ticket au niveau de l'application associée uniquement lors de la mise à jour de l'application, pas lors de sa création.  
  
 Seul un administrateur de l’authentification unique peut configurer des tickets au niveau du système d’authentification unique et au niveau de l’Application associée.  
  
 Si les tickets sont désactivés au niveau du système, ils ne peuvent pas être utilisés non plus au niveau de l'application associée. Il est possible d’activer les tickets au niveau du système et de désactiver au niveau de l’Application associée.  
  
 Si la validation des tickets est activée au niveau du système, elle est également obligatoire au niveau de l'application associée. Il est possible de désactiver la validation des tickets au niveau du système et de l'activer au niveau de l'application associée.  
  
 Si un délai d'expiration du ticket est spécifié tant au niveau du système qu'au niveau de l'application associée, c'est celui qui est défini au niveau de l'application associée qui est utilisé pour déterminer la durée d'expiration du ticket.  
  
 Pour plus d’informations sur les tickets et leur validation, consultez [Tickets SSO](../core/sso-tickets.md).  
  
### <a name="to-configure-the-enterprise-single-sign-on-tickets-using-the-mmc-snap-in-for-the-affiliate-application"></a>Pour configurer les tickets d'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC pour l'application associée  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d’étendue d’enfichable MMC ENTSSO, développez le **Applications associées** nœud.  
  
3.  Avec le bouton droit **Application associée**, puis cliquez sur **propriétés**.  
  
4.  Cliquez sur le **Options** onglet.  
  
5.  Sélectionnez **autoriser les Tickets** et configurez le délai d’attente du ticket comme il convient.  
  
### <a name="to-configure-the-enterprise-single-sign-on-system-level-tickets-using-the-command-line"></a>Pour configurer les tickets au niveau système d'authentification unique de l'entreprise à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – tickets \<autorisée Oui/non\>  *\<valider oui/non\>***, où  *\<autorisée Oui/non \>*  indique si les tickets seront autorisés ou non, et  *\<valider oui/non\>*  indique si les tickets devront être validés après leur échange .  
  
    > [!NOTE]
    >  Vous pouvez utiliser les mots Yes, No, On ou Off pour indiquer s'il convient d'autoriser ou de valider des tickets. Ces mots, dont la casse est indifférente, doivent être utilisés indépendamment de vos paramètres de langue.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’authentification unique](../core/understanding-sso.md)   
 [Utilisation de l’authentification unique](../core/using-sso.md)