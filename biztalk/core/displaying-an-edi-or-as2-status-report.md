---
title: "Afficher un EDI ou le rapport d’état AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60968c3d-6329-411f-9f10-1dd4a6cc9d79
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0564a5c5d904a217ac406befebd3d7c742dc00c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="displaying-an-edi-or-as2-status-report"></a>Affichage des rapports d'état EDI ou AS2
Si les rapports d'état EDI et AS2 sont désactivés, vous avez accès aux rapports d'état suivants :  
  
|Type de rapport|Rapport d'état de niveau supérieur|Rapport d'état de niveau inférieur|  
|--------------------|---------------------------------|--------------------------------|  
|Routage|Échange EDI et état ACK corrélé|-Échange d’état et les détails de l’accusé de réception<br /><br /> -Détails du document informatisé<br /><br /> -Contenu du Message EDI|  
|Routage|état du lot ;|-|  
|Routage|Rapport d'agrégation de l'échange|-|  
|Routage|Rapport d'agrégation du document informatisé|-|  
|AS2|Message AS2 et état MDN corrélé|Contenu du message AS2|  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :  
  
-   Pour personnaliser les rapports d'état, vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Si vous ouvrez une session en tant que membre du groupe Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez afficher les rapports d'état en lecture seule.  
  
## <a name="display-an-edi-or-as2-status-report"></a>Afficher un rapport d’état EDI ou AS2  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur le **groupe BizTalk** nœud.  
  
2.  Dans le **Hub du groupe** onglet de la **vue d’ensemble du groupe** page de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, accédez au bas de la page.  
  
3.  Pour afficher le **échange EDI et état ACK corrélé** de rapports, procédez comme suit :  
  
    1.  Cliquez sur **échange EDI et état ACK corrélé** dans les **rapports d’état EDI** zone de la **Hub du groupe** onglet.  
  
    2.  Pour afficher les détails d’un échange et ses accusés de réception corrélés, cliquez sur une entrée dans les résultats de la **échange EDI et état ACK corrélé** de rapports, puis cliquez sur **état et l’accusé de réception de l’échange détails**.  
  
    3.  Pour afficher les détails d’un document informatisé, fermez l’échange état et l’accusé de réception détails de l’état, retour à la **échange EDI et état ACK corrélé** de rapport détaillé. Cliquez sur une entrée dans les résultats de requête, puis cliquez sur **détails du document informatisé**.  
  
    4.  Pour afficher plus d’informations sur les en-têtes et la charge utile d’un document informatisé, cliquez sur une entrée dans le **détails du document informatisé** de rapports, puis cliquez sur **vue de contenu du document informatisé**.  
  
    5.  Pour afficher les données relatives à l’échange contenant le document informatisé, cliquez sur une entrée dans le **détails du document informatisé** de rapports, puis cliquez sur **état échange/ACK**. L'échange contenant le document informatisé est mis en surbrillance dans le rapport État de l'échange/de l'accusé de réception.  
  
4.  Pour afficher le **état du lot** de rapports, procédez comme suit :  
  
    1.  Cliquez sur **état du lot** dans les **rapports d’état EDI** zone de la **Hub du groupe** onglet.  
  
    2.  Pour afficher les lots terminés associés à une entrée de lot dans le **état du lot** de rapports, cliquez sur l’entrée, puis sur **lots terminés**.  
  
    3.  Pour afficher les données relatives à un échange par lot terminé, cliquez sur l’échange dans le **lot terminé** de rapports, puis cliquez sur **état échange/ACK**. L'entrée associée à l'échange par lot est mis en surbrillance dans le rapport État de l'échange/de l'accusé de réception.  
  
5.  Pour afficher le **rapport d’agrégation d’échange**, procédez comme suit :  
  
    -   Cliquez sur **rapport d’agrégation d’échange** dans les **rapports d’état EDI** zone de la **Hub du groupe** onglet.  
  
6.  Pour afficher le **rapport d’agrégation du document informatisé**, procédez comme suit :  
  
    -   Cliquez sur **rapport d’agrégation du document informatisé** dans les **rapports d’état EDI** zone de la **Hub du groupe** onglet.  
  
7.  Pour afficher le **Message AS2 et état MDN corrélé** de rapports, procédez comme suit :  
  
    1.  Cliquez sur **Message AS2 et état MDN corrélé** dans les **rapports d’état EDIINT** zone de la **Hub du groupe** onglet.  
  
    2.  Pour afficher l’état de l’échange EDI dans un message AS2, cliquez sur une entrée dans le **Message AS2 et état MDN corrélé** de rapports, puis cliquez sur **état échange/ACK**.  
  
        > [!NOTE]
        >  Pour plus d’informations sur la corrélation entre les États EDI et état AS2, consultez la section « Mise en corrélation un AS2 Message avec une charge EDI » de [Message AS2 et rapport d’état MDN corrélé](../core/as2-message-and-correlated-mdn-status-report.md).  
  
    3.  Pour afficher un message AS2 au format câble, cliquez sur une entrée dans le rapport d’état AS2/MDN, puis cliquez sur **Message au Format câble**.  
  
    4.  Pour afficher un message AS2 au format décodé, cliquez sur une entrée dans le rapport d’état AS2/MDN, puis cliquez sur **Message au Format décodé**.  
  
    5.  Pour afficher un message MDN, cliquez sur une entrée dans le rapport d’état AS2/MDN, puis cliquez sur **Mdn Message**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance des Solutions EDI et AS2](../core/monitoring-edi-and-as2-solutions.md)   
 [EDI et AS2 le rapport d’état](../core/edi-and-as2-status-reporting.md)   
 [L’activation des rapports d’état AS2 et EDI](../core/enabling-edi-and-as2-status-reports.md)   
 [Configuration d’un EDI et le rapport d’état AS2](../core/configuring-an-edi-and-as2-status-report.md)