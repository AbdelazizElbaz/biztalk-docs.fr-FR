---
title: "Comment configurer des Options avancées pour un Port d’envoi de Transport | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, transport options [send ports]
- configuring, send ports
- send ports, transport options
- managing [send ports], configuring
- managing [send ports], transport options
ms.assetid: b0033e09-3c18-4e53-a470-e12978e61ba1
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 320ed6c1caf288ac1bf9745a351bbd53a46f48db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-transport-advanced-options-for-a-send-port"></a>Configuration des options avancées de transport pour un port d'envoi
La console Administration de BizTalk Server permet de configurer des options avancées pour un port d’envoi de transport. Ces options déterminent le traitement des messages par le port d'envoi, tel que le nombre de tentatives d'envoi des messages lors d'échecs et la planification de la fenêtre de service pour le port.  
  
> [!NOTE]
> **En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous pouvez activer la livraison chronologique des messages pour les ports d’envoi dynamique, selon le type de carte. Cette option est uniquement disponible pour les types de carte où la livraison chronologique des messages sont garanti pour les ports d’envoi statiques, telles que l’adaptateur de fichier ou de l’adaptateur FTP.
> 
> Considérez les six messages : M1, M2, M3, M4, M5 et M6. M1, M3, M5 sont destinés à un emplacement de fichier. M2 M4 et M6 sont destinés à FTP. Le port d’envoi dynamique de livraison chronologique des messages permet de s’assurer que M1, M3 et M5 sont triées ; et M2 M4 et M6 sont classées respectivement. 
> 
> Pour les types de carte qui ne prennent pas en charge la livraison chronologique, il ne sont pas toutes les propriétés de port d’envoi dynamique disponibles pour la configuration. Les options de transport sont déterminées automatiquement au moment de l’exécution.  
>
> **Pour les versions précédentes de BizTalk** qui utilisent des ports dynamiques, il ne sont pas toutes les propriétés available configurer, car les options de transport sont déterminées automatiquement au moment de l’exécution.

  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="controlling-send-port-priority"></a>Contrôle de la priorité du port d'envoi  
 Le paramètre Priorité des options avancées de transport contrôle l'ordre dans lequel les messages sont supprimés de MessageBox. Les ports dont la priorité est élevée sont traités avant les autres. Ils sont plus importants que les autres ports sur un même hôte.  
  
 La priorité s'avère utile dans les scénarios exigeant des délais de réponse courts pour certains types de requête. Par exemple, si plusieurs ports se connectent à différents systèmes pour traiter des requêtes normales et des requêtes interactives, ces dernières exigeant une réponse rapide, vous souhaitez que ce type de requête soit traité dès que possible.  
  
 BizTalk Server ne traite pas de manière égale les messages dont les priorités sont différentes dans MessageBox. Si MessageBox contient un même nombre de messages avec deux priorités différentes au moment du traitement, les éléments ayant une faible priorité ne seront traités qu'une fois le traitement des éléments ayant une priorité élevée terminé. Si le nombre d'éléments dont la priorité est élevée est important, les éléments ayant une faible priorité risquent de ne jamais être traités. Il manquera des éléments à faible priorité.  
  
> [!WARNING]
>  Pour réduire le risque de manque des messages, testez rigoureusement votre application en condition de charge réelle pour vous assurer que tous les messages sont traités. Dans le cas contraire, des messages risquent de ne pas être traités.  
  
 BizTalk Server affecte de manière interne une priorité à chaque abonnement. Les priorités vont de 1 (priorité la plus élevée) à 10 (priorité la plus faible). La priorité par défaut étant 7 pour l'activation des abonnements et 5 pour la corrélation des abonnements, les messages de corrélations sont délivrés avant ceux d'activation des abonnements.  
  
## <a name="configure-the-transport-options"></a>Configurer les options de transport 
  
1.  Ouvrez **Administration de BizTalk Server.**  
  
2.  Développez le groupe BizTalk, puis développez votre application BizTalk.  
  
3.  Sélectionnez **Ports d’envoi**, cliquez sur le port d’envoi à configurer, puis sélectionnez **propriétés**.  
  
4.  Dans le volet gauche, sélectionnez **Options avancées de Transport**.  
  
5.  Configurez les options de transport comme décrit dans le tableau suivant, puis sélectionnez **OK**.  Seules certaines des propriétés suivantes sont disponibles pour les ports d’envoi dynamiques.
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nombre de tentatives**|Indiquer le nombre de tentatives d'envoi d'un message en cas d'échec du message pour le port d'envoi. La valeur par défaut est 3. la plage autorisée est comprise entre 0 et 1 000.|  
    |**Intervalle avant nouvelle tentative**|Indiquer l'intervalle (en minutes) devant séparer chaque tentative d'envoi du message. La valeur par défaut est de 5 ; la plage autorisée est de 0 à 525 600.|  
    |**Priorité**|Définir la priorité de la tentative de renvoi.|  
    |**Livraison chronologique des messages**|Activer cette case à cocher pour envoyer les messages dans l'ordre de leur réception.|  
    |**Arrêter d’envoyer des messages supplémentaires en cas d’échec de message en cours**|Activer cette case à cocher pour arrêter l'envoi des messages après l'échec d'un message. Cette option est disponible uniquement lorsque le **livraison chronologique des messages** option est sélectionnée.|  
    |**Activer le routage des messages ayant échoué**|Sélectionner cette option pour activer le routage des messages ayant échoué.|  
    |**Activer la fenêtre de service**|Spécifier la période quotidienne pendant laquelle le port d'envoi est opérationnel en indiquant une heure de début et de fin.|  
    |**Heure de début**|Spécifier l'heure quotidienne à partir de laquelle le port d'envoi commence à envoyer les messages. Cette option est disponible uniquement lorsque le **activer la fenêtre de service** option est sélectionnée.|  
    |**Heure de fin**|Spécifier l'heure quotidienne à laquelle le port d'envoi cesse d'envoyer des messages. Cette option est disponible uniquement lorsque le **activer la fenêtre de service** option est sélectionnée.|  
  
## <a name="see-also"></a>Voir aussi  
[Livraison chronologique des messages](../core/ordered-delivery-of-messages.md)  
 [Création et configuration des Ports d’envoi](../core/creating-and-configuring-send-ports.md)