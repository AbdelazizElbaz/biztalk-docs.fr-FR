---
title: "Comment modifier les paramètres généraux | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Bts10.settings.HostGeneral
ms.assetid: f0c90b44-e713-4d27-b125-833a747ab758
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a07a49d4905b13c33f87dcc694ca69c1a044fd2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-general-settings"></a>Modification des paramètres généraux
Le panneau de configuration permet de modifier les paramètres de configuration générale d'un hôte donné à l'intérieur d'un groupe BizTalk. Cette rubrique contient une procédure pas à pas permettant d'effectuer cette opération.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
### <a name="to-modify-the-general-settings-of-a-host"></a>Pour modifier les paramètres généraux d'un hôte  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **hôtes** , cliquez sur le **général** onglet.  
  
3.  Procédez comme suit, puis cliquez sur **appliquer** pour appliquer les modifications et passer à un autre onglet. Ou cliquez sur **OK** pour appliquer les modifications et quitter le panneau de configuration.  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |Hôte|Dans la liste déroulante, sélectionnez l'hôte représentant les instances d'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|-|-||  
    |**Déplacer les données de suivi pour la base de données DTA**|Indiquez si l'hôte charge le composant de suivi BizTalk pour traiter les données d'analyse du fonctionnement et d'entreprise.<br /><br /> Si vous activez cette case, l'hôte actuel disposera d'un accès en lecture et en écriture aux tables de suivi de la base de données MessageBox et à la base de données des suivis. Par conséquent, les objets exécutés sur cet hôte bénéficieront aussi d'un accès en lecture/écriture à ces bases de données.<br /><br /> Si vous désactivez cette case, l'hôte disposera uniquement d'un accès en écriture aux tables de suivi de la base de données MessageBox mais d'aucun accès à la base de données des suivis BizTalk.|Activé, désactivé|Actif||  
    |**Authentification de confiance**|Indiquez si un hôte BizTalk est autorisé à collecter les informations d'authentification.<br /><br /> En spécifiant les hôtes approuvés et qui ne sont pas, vous pouvez définir les limites de sécurité dans laquelle l’utilisateur les objets et le code peuvent être approuvés ou non approuvés.|Activé, désactivé|Inactif||  
    |**32 bits uniquement**|Indiquez si le processus de l'instance de l'hôte doit être créé en tant que processus 32 bits sur les serveurs 32 bits et 64 bits.|Activé, désactivé|Actif||  
    |**Domaine d’application par défaut pour un adaptateur isolé**|Indiquez si l'adaptateur isolé est exécuté dans le domaine d'application par défaut, ou le domaine de l'appelant.<br /><br /> Par défaut, tous les objets du moteur de messagerie sont créés dans le domaine de l'appelant. Si le service Web est inactif pendant une période prolongée, quelle qu'en soit la raison, IIS décharge le domaine de l'appelant. Dans ce cas, tous les services du processus d'hébergement deviennent inutilisables.<br /><br /> Lorsque vous sélectionnez le domaine d'application AppDomain par défaut, les objets du moteur de messagerie BizTalk sont créés dans le domaine d'application AppDomain par défaut et non dans leur propre AppDomain. Par ailleurs, le domaine d'application AppDomain par défaut n'est jamais déchargé.<br /><br /> Cette option devient uniquement disponible après avoir créé l'une des instances de l'hôte dans le domaine d'application AppDomain par défaut.|Activé, désactivé|Inactif|TRUE si l'une des instances de l'hôte est définie sur cette valeur. Sinon, la valeur est FALSE.|  
    |**Comportement des espaces blancs hérité**|Spécifiez si vous souhaitez conserver les espaces blancs lors de la création des mappages.|Activé, désactivé|Inactif|Pour chaque instance d'hôte d'un ordinateur, la valeur est TRUE si l'ordinateur a la valeur de Registre > 0. Pour chaque hôte, la valeur est TRUE si l'une des instances d'hôte a ce paramètre défini sur TRUE.|  
    |**Autoriser les réponses multiples**|Indiquez si vous souhaitez activer le renvoi de réponses multiples à un emplacement de réception bidirectionnel.|Activé, désactivé|Inactif|Si ce paramètre est défini sur TRUE pour l'une des instances de l'hôte, définissez le paramètre de l'hôte = TRUE. Dans le cas contraire, la valeur est FALSE.|  
    |**Délai d’attente de réponse**|Spécifiez le délai d'expiration par défaut des messages de réponse.|1 – Valeur maximale de type entier|20|Hôtes In-process - valeur la plus haute pour une instance de l'hôte<br /><br /> Hôtes isolés - valeur la plus haute sur un ordinateur|  
    |**Threads de moteur maximal**|Indiquez le nombre maximal de threads du moteur de messagerie par UC.<br /><br /> Cette option indique le nombre maximal de threads qui peuvent être utilisés par le Gestionnaire des points de terminaison. Ce dernier commence par le nombre de threads équivalent à 10 % de cette valeur, puis ajoute des threads à concurrence de la valeur spécifiée au fur et à mesure que la charge augmente. Le nombre de threads alloués est réduit au fur et à mesure que la charge est réduite ou selon les exigences de la limitation.<br /><br /> **Remarque** si vous modifiez cette valeur, l’ordinateur hôte doit être redémarré pour que la modification prenne effet.|[1,50]|20|-|  
    |**Afficher les compteurs de performances pour**|Sélectionnez le service pour lequel vous souhaitez afficher les compteurs de performance.<br /><br /> Lorsque l’analyseur de performances est défini sur Messagerie, il affiche les compteurs de l’agent des messages pour la messagerie. Si l’hôte contient des orchestrations, aucune sortie de l’agent des messages n’est affichée pour les instances (XLANG) d’orchestration.<br /><br /> Si l’ordinateur hôte contient uniquement des orchestrations, modifiez le **afficher les compteurs de performances pour** paramètre aux Orchestrations pour afficher les compteurs de l’Agent de Message pour les instances d’Orchestration. Si l’hôte contient uniquement des ports d’envoi ou de réception, conservez l’option Messagerie de manière à afficher les compteurs de l’agent des messages pour les instances de messagerie.|Messagerie, Orchestrations|Messagerie|Si toutes les instances d'un hôte ont la même valeur, utilisez la même valeur pour l'hôte. S'il existe un conflit ou si aucune valeur n'a été définie, utilisez la valeur par défaut.|  
  
     **Intervalles d’interrogation**  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Messagerie**|Définissez l'intervalle d'interrogation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en millisecondes lorsque l'instance de l'hôte BizTalk recherche de nouveaux messages dans la base de données MessageBox.|1 – Valeur maximale de type entier|500|Valeur existante|  
    |**Orchestrations**|Définissez l'intervalle d'interrogation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en millisecondes lorsque l'instance de l'hôte BizTalk recherche de nouvelles orchestrations dans la base de données.|1 – Valeur maximale de type entier|500|Valeur existante|  
  
    > [!NOTE]
    >  Pour restaurer les paramètres par défaut, cliquez sur **restaurer les valeurs par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les paramètres de l’hôte](../core/how-to-modify-host-settings.md)