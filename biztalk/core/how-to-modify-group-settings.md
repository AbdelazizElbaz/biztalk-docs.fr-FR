---
title: "Les paramètres de groupe de mise à jour | Documents Microsoft"
description: "Modifier les paramètres de performances du groupe à l’aide de la console Administration de BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe0cbeb8-23d6-45cf-8535-c989914f5124
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d5de48a504d649279a2e9e0184ff2069547f36a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-biztalk-group-settings"></a>Comment mettre à jour les paramètres du groupe BizTalk
Le panneau de configuration permet de modifier les informations de configuration de tous les ordinateurs à l'intérieur d'un groupe BizTalk. Cette rubrique contient une procédure pas à pas permettant de modifier les paramètres de performance au niveau du groupe dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ces paramètres s'appliquent à tous les ordinateurs d'un groupe donné.  
  
> [!NOTE]
>  Vous pouvez également modifier les paramètres de l'hôte et de l'instance de l'hôte. Pour plus d’informations, consultez [comment modifier les paramètres de l’hôte](../core/how-to-modify-host-settings.md) et [comment modifier les paramètres d’hôte Instance](../core/how-to-modify-host-instance-settings.md).  
  
 Vous pouvez exporter les paramètres actuels de BizTalk Server dans un fichier XML. Plus tard, vous pourrez les importer dans le panneau de configuration au lieu de configurer de nouvelles valeurs. Pour plus d’informations sur l’importation ou l’exportation de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] paramètres, voir [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) et [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md). 
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette opération, vous devez être connecté en tant que membre du groupe Administrateurs de BizTalk Server.  
  
## <a name="update-the-group-level-settings"></a>Mettre à jour les paramètres au niveau du groupe  
  
1.  Dans le **Console d’Administration de BizTalk Server**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **paramètres**.  
  
2.  Dans le **Panneau de configuration BizTalk** boîte de dialogue le **groupe** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|Valeurs limites|Valeur par défaut|Mise à jour de la logique|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Intervalle d’actualisation de configuration**|Définissez l'intervalle auquel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] actualise la configuration de la messagerie.|1 - 43200|-|-|  
    |**Seuil de lot de messages**|Si la taille totale du lot de messages entrants dépasse cette valeur, celui-ci est fractionné en lots plus petits, puis traité.|1 - 10000000|102400|Copie la valeur HKEY_LOCAL_MACHINE\Software\Microsoft\BizTalk Server\3.0\Administration\TransformThreshold|  
    |**Taille de message volumineux**|Définissez la taille limite d'un message individuel qui déclenche un flux dans un lot et/ou au cours des transformations.|1 - 10000000|1000000|Maximale existants **taille de message volumineux** et **LargeMessageFragmentSize** valeurs.|  
    |**Le suivi et création de rapports**||-|-|-|  
    |**Intervalle d’échantillonnage du compteur de performance message boîte**|Définissez l'intervalle d'actualisation des compteurs de performance.<br /><br /> L'intervalle transmet la charge de la base de données pour la mise à jour des compteurs. Une valeur supérieure signifie une fréquence de mise à jour inférieure, et donc un chargement de base de données réduit.|1 – Valeur maximale de type entier|-|Valeur la plus grande sur tous les ordinateurs du groupe BizTalk, le cas échéant. Sinon, valeur par défaut.|  
    |**Activer le suivi au niveau de groupe**|Sélectionnez cette option pour activer le suivi au niveau du groupe pour BizTalk Server.<br /><br /> La désactivation du suivi global désactive les intercepteurs de suivi pour l'intégralité du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cela signifie que BizTalk n'effectue plus le suivi des événements dans les tables de suivi. **Remarque :** ce paramètre n’affecte pas le suivi BAM.|Activé, désactivé|Actif|-|  
  
3.  Cliquez sur **appliquer** pour appliquer les modifications et passer à un autre onglet. Ou cliquez sur **OK** pour appliquer les modifications et quitter le panneau de configuration.  
  
    > [!NOTE]
    >  Pour restaurer les paramètres par défaut, cliquez sur **restaurer les valeurs par défaut**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisez le panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)