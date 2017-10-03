---
title: "Pour configurer les Gestionnaire de réception HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions, receive handlers
- configuring [HTTP adapters], permissions
- HTTP adapters, receive handlers
- receive handlers, permissions
- configuring [HTTP adapters], receive handlers
- permissions, HTTP adapters
- receive handlers, HTTP adapters
- HTTP adapters, permissions
ms.assetid: c295489e-dbbb-44f7-bddb-d3cdfe302cf5
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0380804039d45efbe3db06b6fc072a3afb8b6b48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-http-receive-handler"></a>Pour configurer les Gestionnaire de réception HTTP
La procédure suivante permet de configurer les propriétés d'un gestionnaire de réception HTTP.  
  
> [!NOTE]
>  Un seul gestionnaire de réception peut être associé à chaque hôte.  
  
> [!NOTE]
>  L'adaptateur de réception HTTP est exécuté dans le contexte d'une instance d'hôte BizTalk isolé.  
  
> [!CAUTION]
>  Lors de l'utilisation des gestionnaires d'adaptateur HTTP ou SOAP, il est recommandé d'installer les instances d'hôte pour ces gestionnaires sur des ordinateurs Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].  
  
### <a name="to-configure-the-general-properties-for-an-http-receive-handler"></a>Pour configurer les propriétés générales d'un gestionnaire de réception HTTP  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez **Cartes**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **HTTP,** dans le volet droit, cliquez sur le Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.  
  
4.  Cliquez sur **propriétés** pour accéder à la **taille du lot** Gestionnaire de réception de propriété pour le protocole HTTP.  
  
5.  Entrez une valeur comprise entre 1 et 256, puis cliquez sur **OK**.  
  
6.  Cliquez sur **OK**.  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] est conçu pour traiter efficacement les lots de messages, pas pour traiter un message unique très rapidement. Aussi, si ce gestionnaire de réception doit être utilisé par des emplacements de réception de requête-réponse/bidirectionnels, vous pouvez réduire la latence en procédant comme suit :  
  
-   Définir le **taille du lot** propriété à une valeur de 1.  
  
-   Réduire le **MaxReceiveInterval** valeur à partir de la valeur par défaut de 500 à une valeur inférieure à 100 pour le **messagerie isolée, XLANG/s,** et **messagerie In-Process** service classes.  Modifications du **adm_ServiceClass** table de la base de données de gestion BizTalk qui contienne un enregistrement pour chacun de ces types de service.  Soyez prudent lorsque vous modifiez ce paramètre, car il s’agit d’une modification de l’échelle du type de service. Ce paramètre spécifie l'intervalle d'interrogation maximal (en millisecondes) auquel l'agent des messages [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] interroge la base de données MessageBox de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] afin de récupérer des messages.  Il est également utilisé par le contrôleur de limitation pour décider si la limitation des messages est requise sous certaines conditions de charge. Dans l'affirmative, le contrôleur de limitation augmente de façon incrémentielle l'intervalle de distribution des messages sur la base des conditions de forte charge sur le système. Ce paramètre n'est pas utilisé dans un système à débit élevé.  Une fois que ces valeurs sont utilisées, l'intervalle passe de la valeur MaxReceiveInteral/10 à la valeur MaxReceiveInterval de façon dynamique.  
  
    > [!NOTE]
    >  Modifier ce paramètre affecte tous les ordinateurs hôtes qui sont créés avec un **Type d’hôte** de **isolé**.  
  
-   Redémarrez le ou les pools d'applications IIS associés aux fonctions de réception HTTP que vous avez configurées.  
  
 Le compte d’ouverture de session pour le **BizTalkServerIsolatedHost** instance d’hôte doit disposer de lecture et d’écriture pour l’ou les répertoires temporaires pour compiler de façon dynamique les fichiers de code-behind utilisés par le protocole HTTP receive, fonction. La procédure suivante permet d'octroyer ces autorisations.  
  
### <a name="to-grant-the-account-for-the-biztalkserverisolatedhost-host-instance-read-and-write-permissions-to-the-temp-directory-of-your-biztalk-server"></a>Pour octroyer les autorisations de lecture et d'écriture sur le répertoire temporaire de votre serveur BizTalk Server au compte de l'instance de l'hôte BizTalkServerIsolatedHost  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **CMD**, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, tapez **définir TEMP** et appuyez sur ENTRÉE pour afficher le répertoire associé à la **TEMP** variable d’environnement.  
  
3.  À l’invite de commandes, tapez **set TMP** et appuyez sur ENTRÉE pour afficher le répertoire associé à la **TMP** variable d’environnement.  
  
 Accordez au compte qui est spécifié comme compte d’ouverture de session pour le **BizTalkServerIsolatedHost** héberger une instance en lecture et écriture pour l’ou les répertoires associés le **TEMP** et  **TMP** variables d’environnement. Pour déterminer le compte d’ouverture de session pour le **BizTalkServerIsolatedHost** de l’instance, dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez  **Groupe BizTalk**, développez **paramètres de plateforme**, développez **Instances d’hôte**, avec le bouton droit le **BizTalkServerIsolatedHost** hôte l’instance dans le volet droit, puis cliquez sur **propriétés**. Le compte d’ouverture de session utilisé pour l’instance d’hôte est répertorié en regard du **ouverture de session** étiquette.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur HTTP](../core/configuring-the-http-adapter.md)