---
title: ApplicationAdapter | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f9b876b-cd37-4e24-a476-186adc155ac0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc2808f8cdc2d24a2f7c13864a153361984d0981
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="applicationadapter"></a>ApplicationAdapter
L’exemple ApplicationAdapter montre comment envoyer des notifications à partir de processus publics et privés (répondeur ou initiateur) lorsque vous recevez un message. Vous pouvez personnaliser l’exemple avec les fonctionnalités supplémentaires que vous souhaitez.  
  
 L’exemple ApplicationAdapter montre comment implémenter la `IApplicationAdapter` de l’interface pour la `ApplicationAdapter1` classe. Cette classe inclut deux méthodes, `BeginNotify` et `Notify`. Les paramètres pour chaque classe sont la catégorie du message, le nom du tiers source, le nom de tiers de destination, le code de processus PIP (Partner Interface), ID d’instance PIP et PIP version.  
  
 Vous définissez le ApplicationAdapter pour un accord en entrant le nom de l’assembly et le nom de classe sur le **général** onglet de l’accord dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] ([!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]) Console de gestion. Le fichier .dll d’application s’exécute sous les mêmes informations d’identification que le service d’hôte BizTalk.  
  
 Si vous modifiez l’exemple ApplicationAdapter ou n’importe quelle variable d’environnement externe qui dépend de l’exemple ApplicationAdapter, redémarrez le service d’hôte BizTalk qui héberge le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus public.  
  
 L’exemple de code ApplicationAdapter se trouve à \< *lecteur*> : \Program Files\ BizTalk \<version > Accelerator for RosettaNet\SDK\ApplicationAdapter\\.  
  
## <a name="demonstrates"></a>Montre  
 L’exemple ApplicationAdapter montre comment notifier le processus privé répondeur que le processus public a reçu un message. La notification indique la catégorie du message, le nom du tiers source, le nom de tiers de destination, le code PIP, la version PIP et l’ID d’instance PIP. Vous pouvez envoyer cette notification pour une action ou un message de réponse.  
  
 Le `BeginNotify` et `Notify` méthodes fonctionnent comme suit :  
  
1.  Le processus public répondeur reçoit un message.  
  
    > [!NOTE]
    >  Les étapes suivantes sont également applicables pour le scénario dans lequel l’initiateur publique reçoit un message de réponse du récepteur.  
  
2.  Si la validation par le pipeline de réception et le processus public et l’adaptateur de validation, le cas échéant, a réussi, le répondeur public traite les appels de la `BeginNotify` méthode dans la `ApplicationAdapter` classe. Cette méthode notifie le processus privé répondeur que le processus public a reçu le message nouvelle et enregistré dans la base de données MessageBox.  
  
3.  Le processus public répondeur envoie un message de signal à l’initiateur.  
  
4.  Le processus public répondeur envoie le contenu du service message au processus privé répondeur.  
  
5.  Le processus privé répondeur place le message dans la table MessagesToLOB de la base de données BTARNDATA.  
  
6.  Les appels de processus privé répondeur le `Notify` méthode dans la `ApplicationAdapter` classe pour envoyer le message de notification de fin au processus publics répondeur. Le processus public répondeur doit recevoir le message de notification de fin, le processus s’est terminé avec succès. Sinon, le message est suspendu.  
  
> [!NOTE]
>  Vous pouvez utiliser le `Notify` message pour signaler à l’application de métier (LOB) que le message est en attente dans la table MessagesToLOB. Le système les alertes dès l’application métier, l’application métier peut récupérer le message à partir de cette table.  
  
## <a name="to-implement-this-sample"></a>Pour implémenter cet exemple  
 Pour implémenter l’exemple ApplicationAdapter, vous devez ajouter l’adaptateur d’application de l’accord.  
  
#### <a name="to-add-the-application-adapter-to-an-agreement"></a>Pour ajouter l’adaptateur d’application à un accord  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] **BizTalk \<version > Accelerator for RosettaNet**, puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans le [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur **accords**.  
  
3.  Double-cliquez sur l’accord auquel vous souhaitez ajouter l’adaptateur d’application.  
  
4.  Dans le **adaptateur d’Application** , cliquez sur le bouton de sélection (**...** ) situé à droite de **nom de l’Assembly**, accédez à l’emplacement qui contient l’assembly de l’adaptateur d’application, sélectionnez le fichier .dll approprié, puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur la flèche vers le bas pour **nom de la classe**, sélectionnez la classe d’adaptateur application, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)