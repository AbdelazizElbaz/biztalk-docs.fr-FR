---
title: "Pour configurer un MSMQ emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, receive locations
- receive locations, MSMQ adapters
- configuring [MSMQ adapters], receive locations
ms.assetid: ba25cf43-18f1-4c19-84fb-74c7b82b95a9
caps.latest.revision: "43"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3a59e64c93e908fce7590f885fe8c38e3a51cf4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-receive-location"></a>Configuration d'un emplacement de réception MSMQ
Vous pouvez définir des variables d'adaptateur d'emplacement de réception MSMQ dans la console Administration de BizTalk Server. Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de BizTalk Server sont utilisées.  
  
> [!NOTE]
>  Avant d'effectuer la procédure suivante, vous devez avoir ajouté un port de réception. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
> [!IMPORTANT]
>  Si une instance de l'hôte est associée à un port d'envoi ou à un emplacement de réception MSMQ, vérifiez que le service MSMQ est en cours d'exécution sur cet ordinateur. Si le service ne fonctionne pas, les ports de réception MSMQ sont fermés peu de temps après leur démarrage, et l'envoi de messages aux ports d'envoi MSMQ est suspendu.  
>   
>  Dans un scénario de mise en cluster, non seulement l'instance MSMQ en cluster doit être en cours d'exécution, mais le service MSMQ sur chaque ordinateur du cluster doit l'être également.  
  
## <a name="to-configure-variables-for-an-msmq-receive-location"></a>Pour configurer les variables d'un emplacement de réception MSMQ  
 Pour configurer les variables d'un emplacement de réception MSMQ, procédez comme suit :  
  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez le vous souhaitez créer un emplacement de réception dans l’application.  
  
2.  Dans la console Administration de BizTalk Server, dans le volet gauche, cliquez sur le **Port de réception** nœud. Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau**pour créer un nouvel emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section regard **Type**, sélectionnez **MSMQ** dans la liste déroulante, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport MSMQ** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|Type de date|Valeur par défaut|  
    |--------------|----------------|---------------|-------------------|  
    |**Mot de passe**|Définir un mot de passe à utiliser pour une file d'attente distante.|Chaîne|Vide|  
    |**Nom d'utilisateur**|Indiquer le nom d'utilisateur à utiliser, en même temps que le mot de passe, pour accéder à une file d'attente distante. Vous ne pouvez pas indiquer ici le nom de l'utilisateur local de l'ordinateur distant.|Chaîne|Vide|  
    |**Taille de lot**|Configurer la taille de lot. L'adaptateur MSMQ envoie des messages par lot à la base de données MessageBox. La taille du lot par défaut est 20, et la taille minimale 1. **Remarque :** si le **transactionnel** pour l’emplacement de réception est définie sur **True**; chaque lot de messages est envoyé à la base de données MessageBox dans le contexte d’un Microsoft Distributed Transaction Transaction Coordinator (MSDTC). La transaction MSDTC qui est créée pour un lot de messages reste ouverte jusqu'à ce que chaque message du lot conservé dans la base de données MessageBox soit placé dans la file d'attente d'abonné appropriée. Par conséquent, la durée de cette transaction MSDTC augmente proportionnellement les **taille de lot** paramètre est augmenté. Dans la mesure où un grand nombre de transactions MSDTC ouvertes simultanément risquant d’affecter les performances globales, les **taille de lot** paramètre ne doit pas être défini à une valeur très élevée lors de la prise en charge de la transaction est activée.|int|20|  
    |**En cas d’échec**|Indiquer comment l'adaptateur doit réagir à une erreur. Définir cette propriété sur l'une des valeurs suivantes :<br /><br /> -   **Arrêter.** la réception des messages via cet emplacement de réception est interrompue si une condition d'erreur se produit.<br />-   **Suspend(non-Resumable).** les messages sont interrompus et marqués comme ne pouvant être repris.<br />-   **Suspend(Resumable).** les messages sont interrompus et marqués comme pouvant être repris. **Important :** si le **True** est définie sur **traitement chronologique** propriété, le **arrêter** est définie sur le **en cas d’échec** propriété et le **False** est définie sur le **transactionnel** propriété sont appliquées en même temps, puis tous les messages dont la remise échouent ne seront pas interrompus ou restant dans la file d’attente source. mais perdus. Pour éviter la perte de données, lorsque vous utilisez la **traitement chronologique** fonctionnalité, le **arrêter** option pour le **en cas d’échec** propriété doit être appliquée uniquement si la **True**  est définie sur le **transactionnel** propriété est appliquée. Par la suite, si la remise d'un message échoue, le message d'origine sera conservé dans la file d'attente MSMQ source. Si le **traitement chronologique** est définie sur une valeur de **False** le **en cas d’échec** propriété ne prendre effet et si un échec de remise de message produit le message est interrompu avec l’état **suspendu (peut être repris)**.|Chaîne|Suspendu (peut être repris)|  
    |**Traitement ordonné**|Définissez cette propriété sur **True** ou **False**. Cette option indique s'il faut traiter les messages en série. La propriété **True** prend en charge les livraison chronologique des messages lorsqu’il est utilisé conjointement avec une orchestration ou la messagerie port d’envoi BizTalk a la **livraison chronologique des messages** lavaleurd’option **True**. Pour plus d’informations, consultez [classés de remise de Messages](../core/ordered-delivery-of-messages.md).<br /><br /> Si cette propriété **True** permet également d’optimiser l’utilisation des ressources lors du traitement des messages volumineux en rendant l’adaptateur monothread. Pour plus d’informations, consultez [envoyer et recevoir des Messages volumineux à l’aide de l’adaptateur MSMQ](../core/sending-and-receiving-large-messages-using-the-msmq-adapter.md).|Booléen|False|  
    |**File d’attente**|Taper un chemin d'accès valide à la file d'attente. En fonction du chemin spécifié, le système effectue les validations appropriées. **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères. **Remarque :** adaptateur de réception MSMQ utilise un mécanisme d’interrogation pour surveiller la file d’attente MSMQ spécifié pour les nouveaux messages toutes les 0,5 secondes. Cet intervalle est fixe.|Chaîne|Vide|  
    |**Transactionnelle**|Définissez cette propriété sur **True** ou **False**. **Remarque :** l’adaptateur prend en charge les lectures transactionnelles des files d’attente distantes avec Message Queuing 4.0 ou version ultérieure uniquement. Dans ce scénario, tant [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] que le serveur Message Queuing distant doivent exécuter Message Queuing 4.0 ou une version ultérieure. <br /><br /> Pour plus d’informations, consultez [configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md) et [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).|Booléen|False|  
  
    > [!NOTE]
    >  Le **nom d’utilisateur** et **mot de passe** s’appliquent uniquement aux comptes Windows utilisés pour accéder aux files d’attente distantes.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, entrez les valeurs appropriées pour terminer la configuration de l’emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md)