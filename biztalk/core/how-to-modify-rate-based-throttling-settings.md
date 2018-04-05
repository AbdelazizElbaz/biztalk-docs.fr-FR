---
title: Comment modifier la fréquence en fonction de paramètres de limitation | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Bts10.settings.HostRate
ms.assetid: a99dfb29-dee6-4a43-8d34-45179d9d0b5e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be54bd3d986143b3f267655bbcb003967e50238f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-rate-based-throttling-settings"></a>Modification des paramètres de la limitation basée sur la fréquence
Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la limitation basée sur la fréquence s'applique aux instances de l'hôte qui contiennent des adaptateurs d'envoi ou des orchestrations qui reçoivent et remettent ou traitent des messages qui ont été publiés dans la base de données MessageBox. Le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] permet de modifier les paramètres de configuration de la limitation basée sur la fréquence d'un hôte donné à l'intérieur d'un groupe BizTalk. Ces paramètres s'appliquent à toutes les instances d'hôte affectées à l'hôte donné. Cette rubrique contient une procédure pas à pas permettant de modifier ces paramètres.  
  
 La condition de limitation basée sur la fréquence peut être déclenchée dans les conditions suivantes :  
  
-   Le volume de mémoire, le nombre de threads ou le nombre de connexions de base de données utilisés par l'instance de l'hôte dépasse les seuils de limitation.  
  
-   La vitesse d'entrée de remise de messages  de l'instance de l'hôte dépasse la vitesse de sortie de remise de messages * la valeur spécifiée de Facteur de dépassement de la vitesse (en pourcentage).  
  
-   Le nombre de messages traités simultanément par l'instance de l'hôte dépasse les Messages In-process par UC * le nombre d'UC disponibles dans la zone.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
### <a name="to-modify-the-rate-based-throttling-settings-of-a-host"></a>Pour modifier les paramètres de la limitation basée sur la fréquence d'un hôte  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **hôtes** , cliquez sur le **limitation basée sur** onglet.  
  
3.  Procédez comme suit, puis cliquez sur **appliquer** pour appliquer les modifications et passer à un autre onglet. Sinon, cliquez sur **OK** pour appliquer les modifications et quitter le panneau de configuration.  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Hôte**|Dans la liste déroulante, sélectionnez l'hôte représentant les instances d'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|-|-|-|  
  
     **Publication**  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Nombre minimal d’exemples**|Spécifiez le nombre minimal de messages [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] va échantillonner pour la **durée de fenêtre d’échantillonnage** avant de considérer la limitation basée sur un taux.<br /><br /> Si le nombre réel d’exemples dans une fenêtre d’échantillonnage se situent sous cette valeur, puis les exemples sont ignorés et la limitation n’est pas appliquée. Cette valeur doit correspondre à la fréquence à laquelle les messages peuvent être publiés sous une charge moyenne. Par exemple, si votre système doit gérer 1 000 documents par seconde sous une charge moyenne, puis ce paramètre doit être défini à 1 000 \* fenêtre durée échantillonnage en secondes (ou plus précisément, 1 \* **fenêtre d’échantillonnage durée** (secondes)). Si cette valeur est trop basse, une condition de limitation risque d'apparaître sous une faible charge. Si elle est trop élevée, il risque de ne pas y avoir suffisamment d'exemples pour que cette technique soit efficace.|1 – Valeur maximale de type entier|100|-|  
    |**Durée de la fenêtre d’échantillonnage**|Spécifiez la fenêtre de temps (mesurée en secondes), utilisée pour calculer la fréquence de publication basée sur les échantillons collectés. Cette durée doit être augmentée si la latence requise pour la publication d'un seul message est élevée.|1 – Valeur maximale de type entier|15000|-|  
    |**Facteur de dépassement de vitesse**|Spécifiez en pourcentage dans quelle mesure vous autorisez la fréquence des demandes à dépasser celle d'exécution avant qu'une condition de limitation soit déclenchée.<br /><br /> Par exemple, si les messages sont publiés à une fréquence de 200 messages par seconde et que la valeur de ce paramètre est de 125, le système autorise la publication de 250 messages au maximum par seconde (125 % * 200 = 250) avant d'appliquer la limitation. Si vous spécifiez une valeur trop petite pour ce paramètre, le système risque d'appliquer une limitation excessive. En spécifiant une valeur trop grande pour ce paramètre peut provoquer sous la limitation et empêcher le mécanisme de limitation de ne pas reconnaître une condition de limitation légitime.|1 – Valeur maximale de type entier|125|-|  
    |**Délai de limitation maximal**|Spécifiez le délai maximal (en millisecondes) imposé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur l'instance d'un message en raison d'une limitation. Le délai réel dépend de la gravité de la condition de limitation.|1 – Valeur maximale de type entier|300000|-|  
    |**Remplacement de limitation**|Spécifiez si vous souhaitez remplacer la limitation de publication de message.|0 : ne pas remplacer<br /><br /> 1 : initialiser la condition de limitation<br /><br /> 2 : ne pas limiter la|0|Les paramètres de limitation lus depuis le Registre doivent être mappés un à un aux paramètres d'instance de l'hôte.|  
    |**Gravité du remplacement de limitation**|Spécifiez la gravité de la condition de limitation au niveau des entrées.<br /><br /> Une valeur supérieure accroît la gravité d’une condition de limitation initiée lorsque **remplacement de limitation** est définie sur 1.|1 – 1000|100|Valeur d'instance de l'hôte la plus faible.|  
  
     **Remise**  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Nombre minimal d’exemples**|Spécifiez le nombre minimal de messages BizTalk va échantillonner pour la **durée de fenêtre d’échantillonnage** avant de considérer la limitation basée sur un taux.<br /><br /> Si, dans la fenêtre d'échantillonnage, le nombre réel d'exemples est inférieur à la valeur indiquée pour ce paramètre, les exemples sont ignorés et la limitation basée sur la fréquence n'est pas appliquée. Cette valeur doit correspondre à la fréquence à laquelle les messages peuvent être remis sous une charge moyenne. Par exemple, si votre système doit gérer 1 000 documents par seconde sous une charge moyenne, puis ce paramètre doit être défini à 1 000 \* fenêtre durée échantillonnage en secondes (ou plus précisément, 1 \* **durée de fenêtre d’échantillonnage**  (en secondes) pour ce scénario).<br /><br /> Si cette valeur est trop basse, une condition de limitation risque d'apparaître sous une faible charge. Si elle est trop élevée, il risque de ne pas y avoir suffisamment d'exemples pour que cette technique soit efficace.|1 – Valeur maximale de type entier|100|-|  
    |**Durée de la fenêtre d’échantillonnage**|Spécifiez la fenêtre de temps (en secondes), utilisée pour calculer la fréquence de traitement basée sur les échantillons collectés. Cette durée doit être augmentée si la latence requise pour le traitement d'un seul message est élevée.|1 – Valeur maximale de type entier|15000|-|  
    |**Facteur de dépassement de vitesse**|Spécifiez en pourcentage dans quelle mesure vous autorisez la vitesse de remise des messages au moteur de messagerie ou d'orchestration à dépasser la vitesse d'exécution avant qu'une condition de limitation soit déclenchée.<br /><br /> Par exemple, si les messages sont traités à une fréquence de 200 messages par seconde et que la valeur de ce paramètre est de 125, le système autorise le traitement de 250 messages au maximum par seconde (125 % * 200 = 250) avant d'appliquer la limitation. En spécifiant une valeur trop faible pour ce paramètre, le système de limitation de façon plus agressive et risque d’être la limitation. Inversement, si vous spécifiez une valeur trop grande, vous obtenez une limitation insuffisante et le mécanisme de limitation risque de ne pas reconnaître une condition de limitation légitime.|1 – Valeur maximale de type entier|125|-|  
    |**Délai de limitation maximal**|Indiquez le délai maximum que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] imposera à une instance de message pour des raisons de limitation. Le délai réel dépend de la gravité de la condition de limitation.|1 – Valeur maximale de type entier|300000|-|  
    |**Remplacement de limitation**|Spécifiez si vous souhaitez remplacer la limitation de remise de message.|0 : ne pas remplacer<br /><br /> 1 : initialiser la condition de limitation<br /><br /> 2 : ne pas limiter la|0|Les paramètres de limitation lus depuis le Registre doivent être mappés un à un aux paramètres d'instance de l'hôte.|  
    |**Gravité du remplacement de limitation**|Spécifiez la gravité de la condition de limitation au niveau des sorties.<br /><br /> Une valeur supérieure accroît la gravité d’une condition de limitation initiée lorsque **remplacement de limitation** est définie sur 1.|1 – 1000|100|Valeur d'instance de l'hôte la plus faible.|  
  
    > [!NOTE]
    >  Pour restaurer les paramètres par défaut, cliquez sur **restaurer les valeurs par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment modifier les paramètres de l’hôte](../core/how-to-modify-host-settings.md)