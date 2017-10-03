---
title: "Leçon 2 : Ajout d’un Port d’envoi XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, XML ports
- XML ports
ms.assetid: 03b2ee43-7874-4ef9-b716-8e16e96d8382
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06b110b911c8cba2dbc643928e8b97e3746935a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-adding-an-xml-send-port"></a>Leçon 2 : Ajout d’un Port d’envoi XML
Un port d’envoi vous permet de définir la façon dont vous souhaitez que les messages envoyés. Dans cette leçon, vous créez un port d’envoi pour définir la façon dont les messages XML doivent être envoyés.  
  
### <a name="to-add-an-xml-send-port"></a>Pour ajouter un port d’envoi XML  
  
1.  Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
2.  Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez **MT103_XML_SendPort**.  
  
3.  Dans le **Transport** section, pour le **Type** zone, cliquez sur la liste déroulante, puis sélectionnez **fichier**.  
  
4.  Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.  
  
5.  Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.  
  
6.  Dans la boîte de dialogue Rechercher un dossier, déplacer vers le  **\<lecteur > : \Labs\Outbound** dossier, puis cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue Propriétés du Transport FILE, vérifiez que **%MessageID%.xml** est entré dans le **nom de fichier** zone, puis cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue Propriétés de Port d’envoi, vérifiez que **BizTalkServerApplication** est sélectionné pour le **Gestionnaire d’envoi** qui **PassThruTransmit** est sélectionné pour le **Pipeline d’envoi** boîte.  
  
9. Dans le volet gauche, cliquez sur **filtres**, puis procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **BTS. ReceivePortName**.|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **MT103_FlatFile_ReceivePort**.|  
    |**Grouper**|Sélectionnez **et**.|  
  
10. Cliquez à l’intérieur de la ligne suivante de la propriété et procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Propriété**|Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**|  
    |**Opérateur**|Sélectionnez  **==** .|  
    |**Valeur**|Type **False** pour les messages valides.|  
  
    > [!NOTE]
    >  Vous ajoutez le **» Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False «** clause d’expression de filtre afin que le port d’envoi envoie uniquement analyser et de valider les messages. Contrairement à un pipeline de réception à l’aide de native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] désassembleurs, les [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] désassembleur ne suspend pas un message (erroné) ayant échoué, mais à la place le publie dans la MessageBox et la marque comme étant a échoué, en utilisant les propriétés promues. A4SWIFT attache une représentation XML des erreurs qui ont été collectés pour le message ayant échoué avant de le publier dans MessageBox.  
    > Sans inclure le « Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed == False « clause d’expression de filtre, votre port d’envoi envoie tous les messages : a réussi ou échoué. Pour plus d’informations sur les abonnements aux messages ayant échoué, consultez [utilisation des abonnements de Message d’échec de](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).  
  
11. Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
12. Dans la Console Administration de BizTalk Server, dans **Ports d’envoi**, avec le bouton droit **MT103_XML_SendPort**, puis cliquez sur **Démarrer**.  
  
 Passez à [Module 6 : déployer les règles d’entreprise](../../adapters-and-accelerators/accelerator-swift/module-6-deploying-the-business-rules.md).