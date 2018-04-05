---
title: Comment modifier la ressource en fonction de paramètres de limitation | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Bts10.settings.HostResource
ms.assetid: 5f8b32a8-d8cc-4045-a8be-0de0bbadcce4
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67207816c96a808118cceb52fc71782955f881cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-resource-based-throttling-settings"></a>Modification des paramètres de la limitation basée sur les ressources
Le panneau de configuration BizTalk permet de modifier les paramètres de configuration de la limitation basée sur les ressources d'un hôte donné à l'intérieur du groupe BizTalk. Ces paramètres s'appliquent à toutes les instances d'hôte affectées à l'hôte donné. Cette rubrique contient une procédure pas à pas permettant de modifier ces paramètres.  
  
 Pour gérer l'utilisation des ressources système (telles que les threads, la mémoire et la taille de la base de données) par un processus de l'instance de l'hôte, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise un mécanisme de limitation réglable qui régit le flux et le traitement de messages sur une instance de l'hôte. Le mécanisme de limitation de l'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de vérifier que le système fonctionne à un niveau optimal et acceptable en :  
  
-   modérant la charge de travail de l'instance de l'hôte ;  
  
-   empêchant le conflit de ressources qui peut réduire les performances globales du processus de l'instance de l'hôte ou d'autres processus système ;  
  
-   détectant à quel moment les ressources disponibles sont sous-utilisées.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
### <a name="to-modify-the-resource-based-throttling-settings-of-a-host"></a>Pour modifier les paramètres de la limitation basée sur les ressources d'un hôte  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **hôtes** , cliquez sur le **limitation basée sur les ressources** onglet.  
  
3.  Procédez comme suit, puis cliquez sur **appliquer** pour appliquer les modifications et passer à un autre onglet. Sinon, cliquez sur **OK** pour appliquer les modifications et quitter le panneau de configuration.  
  
    |**Utilisez cette**|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |------------------|----------------|---------------------|-------------------|-------------------|  
    |**Hôte**|Dans la liste déroulante, sélectionnez l'hôte représentant les instances d'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|-|-|-|  
    |**Paramètres par UC**||-|-|-|  
    |**Threads**|Spécifier le nombre maximal de threads autorisés dans le processus (par UC) avant que la limitation ne démarre.|(0, Valeur maximale de type entier)|0|-|  
    |**Connexions de base de données**|Spécifier le nombre maximal de sessions de base de données (par UC) avant que la limitation ne démarre.|1 – Valeur maximale de type entier|0|-|  
    |**Messages in-process**|Spécifier le nombre maximal de messages remis au Gestionnaire des points de terminaison ou à XLANG qui n'ont pas été traités. Cela n'inclut pas les messages extraits de la base de données, mais toujours en attente de remise dans la file d'attente en mémoire.|1 – Valeur maximale de type entier|1000|-|  
    |**Taille de file d’attente de messages internes**|Indiquer la taille de la file d'attente en mémoire. Cette file d'attente sert d'espace réservé temporaire pour la remise des messages.<br /><br /> La définition d'une valeur élevée pour ce paramètre peut améliorer, dans une certaine mesure, des scénarios de latence faible, étant donné que davantage de messages vont être récupérés de façon proactive de la base de données MessageBox pour traitement. Comme les messages de cette file d'attente consomment de la mémoire, la définition de ce paramètre sur une valeur inférieure est sans doute préférable dans des scénarios impliquant des messages volumineux pour éviter la limitation du processus basée sur la mémoire. **Remarque :** si vous modifiez cette valeur, l’ordinateur hôte doit être redémarré pour que la modification prenne effet.|1 – Valeur maximale de type entier|100|-|  
    |**Nombre de messages dans la base de données**|Indiquer le nombre total de messages publiés par cette instance de l'hôte dans les files d'attente de travail, de messages interrompus et d'état des hôtes d'abonnement.<br /><br /> Le **nombre dans la base de données de messages** définissant également indirectement définit le seuil pour une condition de limitation en fonction du nombre de messages dans la table de mise en attente ou de la table de suivi. Si le nombre de messages dans la table de mise en file d'attente ou dans la table de suivi dépasse 10 fois cette valeur, une condition de limitation est déclenchée.|1 – Valeur maximale de type entier|50000|-|  
    |**Utilisation de la mémoire**||-|-|-|  
    |**Mémoire physique globale**|Spécifier (en pourcentage) l'utilisation de mémoire virtuelle système maximale autorisée avant que la limitation ne démarre.|0: disable<br /><br /> 1% – 100%<br /><br /> Les valeurs > 100% sont traitées comme des Mo et peuvent atteindre la valeur maximale entière|0|-|  
    |**Mémoire virtuelle de processus**|Spécifier la mémoire de processus maximale (en pourcentage) autorisée avant que la limitation ne démarre (en pourcentage ou mégaoctets).|0: disable<br /><br /> 1% – 100%<br /><br /> Les valeurs > 100% sont traitées comme des Mo et peuvent atteindre la valeur maximale entière|25|-|  
    |**Multiplicateur de mise en attente**|Indiquer le facteur par lequel la **nombre dans la base de données de messages** seuil est multiplié, puis comparé le nombre actuel d’enregistrements dans la table du spouleur.<br /><br /> Ceci permet de déterminer si le système doit limiter en fonction de la taille de cette table. Si cette valeur est définie sur 0, la taille de la table de mise en attente n'est pas utilisée pour déterminer une condition de limitation.|0-1000|10|Les paramètres de limitation lus depuis le Registre doivent être mappés un à un aux paramètres d'instance de l'hôte.|  
    |**Multiplicateur de données de suivi**|Spécifiez le facteur par lequel la **nombre dans la base de données de messages** seuil est multiplié, puis comparé le nombre actuel d’enregistrements dans la table de suivi.<br /><br /> Cela est effectuée pour déterminer si le système doit limiter en fonction de la taille de la table de suivi. Si cette valeur est définie sur 0, la taille de la table de suivi n'est pas utilisée pour déterminer une condition de limitation.|0-1000|10|Les paramètres de limitation lus depuis le Registre doivent être mappés un à un aux paramètres d'instance de l'hôte.|  
    |**Limite de déclenchement du catalogue global**|Spécifier à quel moment un nettoyage de la mémoire .NET est déclenché à mesure que l'utilisation de la mémoire de processus augmente et s'approche du seuil. Lorsque l'utilisation de la mémoire dépasse cette valeur de pourcentage du seuil de mémoire, un nettoyage forcé .NET (garbage collection) est déclenché.|50-100|80|Les paramètres de limitation lus depuis le Registre doivent être mappés un à un aux paramètres d'instance de l'hôte.|  
    |**Seuil de mémoire par lots**|Indiquer (en pourcent) le seuil de mémoire au-delà duquel la publication d'un lot de messages doit être limitée.<br /><br /> Le seuil de mémoire par lots est calculé en multipliant ce pourcentage par le **virtuelle de processus** seuil. Si la mémoire estimée pour exécuter un lot de publication dépasse le seuil de mémoire par lots, le lot est soumis à une limitation basée sur la mémoire de processus. Dans le cas contraire, il est exempt de limitation même lorsque la mémoire de processus totale dépasse le **virtuelle de processus** seuil.<br /><br /> La valeur zéro indique que tous les lots de publication peuvent être soumis à une limitation basée sur la mémoire de processus même si la mémoire estimée pour exécuter le lot est minime.|0%-100%||Les paramètres de limitation lus depuis le Registre doivent être mappés un à un aux paramètres d'instance de l'hôte.|  
    |**Severity**||-|-|-|  
    |**Mémoire**|Indiquer la gravité d'une condition de limitation déclenchée par une mémoire de processus. Spécifié sous forme de pourcentage, ce paramètre définit la gravité d’une condition de limitation déclenchée lorsque le **virtuelle de processus** seuil est dépassé.|1 – 1000|500|Valeur d'instance de l'hôte la plus faible|  
    |**Taille de la base de données**|Indiquer la gravité d'une condition de limitation déclenchée par la taille d'une base de données. Spécifié sous forme de pourcentage, ce paramètre définit la gravité d’une condition de limitation déclenchée lorsque le **nombre dans la base de données de messages** seuil est dépassé.|1 – 1000|1|Valeur d'instance de l'hôte la plus faible|  
    |**Message à la volée**|Spécifiez le temps de réaction de la limitation lorsque la valeur de **messages In-process** dépasse le seuil. Est spécifié en tant que pourcentage et ce paramètre définit la gravité d’une condition de limitation déclenchée lorsque la valeur de **messages In-process** seuil est dépassé.|1 – 1000|75|Valeur d'instance de l'hôte la plus faible|  
  
    > [!NOTE]
    >  Pour restaurer les paramètres par défaut, cliquez sur **restaurer les valeurs par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les paramètres de l’hôte](../core/how-to-modify-host-settings.md)