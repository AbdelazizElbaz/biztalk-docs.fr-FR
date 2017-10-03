---
title: "Configurer les propriétés de liaison pour Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding properties, specifying at design time
- binding properties, specifying at run time
- how to, specify binding properties at design time
- how to, specify binding properties at run time
ms.assetid: 063e9507-8172-4fb0-8b9f-2f95e8a82f21
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b26e9e89319a14317113b730adb189f2f17587f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-binding-properties-for-siebel"></a>Configurer les propriétés de liaison pour Siebel
Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose plusieurs propriétés de liaison qui vous permettent de contrôler certaines de ses caractéristiques de comportement. Cette section fournit des informations sur la définition des propriétés de liaison à partir de Visual Studio (conception) et de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’Administration (temps d’exécution). Au moment du design, vous devez spécifier les propriétés de liaison pour générer le schéma pour des opérations spécifiques. Au moment de l’exécution, vous devez spécifier les propriétés de liaison en tant que partie du port d’envoi pour envoyer des messages au système Siebel.  
  
 Pour plus d’informations sur les propriétés de liaison, notamment une liste de propriétés de liaison pour [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
## <a name="enter-the-binding-properties-at-design-time"></a>Entrez les propriétés de liaison au moment du design  
 Pour le moment du design, vous devez spécifier les propriétés de liaison à partir de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] boîte de dialogue.  
  
#### <a name="enter-binding-properties-using-consume-adapter-service-add-in"></a>Entrez les propriétés de liaison à l’aide de complément Consume Adapter Service  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **siebelBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet et spécifier les valeurs de liaison, si elle existe, qui sont nécessaires pour être spécifié avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
6.  Cliquez sur **OK**.  
  
#### <a name="enter-binding-properties-using-add-adapter-metadata-wizard"></a>Entrez les propriétés de liaison à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
    |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
3.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
4.  Dans l’Assistant Ajout d’adaptateur, sélectionnez **WCF-Siebel**. Sélectionnez l’ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] est installé et le nom de la base de données BizTalk.  
  
    > [!IMPORTANT]
    >  Si vous disposez déjà d’un port WCF-Siebel configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **siebelBinding**, puis cliquez sur **configurer**.  
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet et spécifier les valeurs de liaison, si elle existe, qui sont nécessaires pour être spécifié avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous avez sélectionné un port d’envoi WCF-Siebel existant, vous ne devez pas spécifier les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
8.  Cliquez sur **OK**.  
  
## <a name="enter-binding-properties-at-run-time"></a>Entrez les propriétés de liaison au moment de l’exécution  
 Temps d’exécution, vous devez spécifier les propriétés de liaison dans le cadre de WCF-Custom ou la configuration du port WCF-Siebel dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
#### <a name="enter-binding-properties-for-the-wcf-custom-port"></a>Entrez les propriétés de liaison de port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** . Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans le **propriétés de Port** boîte de dialogue, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
5.  À partir de la **Type de liaison** la liste déroulante, sélectionnez **siebelBinding**.  
  
6.  Dans le **Configuration** zone, spécifiez les valeurs pour les propriétés de liaison différente, cliquez sur **OK**.  
  
#### <a name="enter-binding-properties-for-the-wcf-siebel-port"></a>Entrez les propriétés de liaison de port WCF-Siebel  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-Siebel à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [ajouter l’adaptateur Siebel à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** . Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans le **propriétés de Port** boîte de dialogue, à partir de la **Type** la liste déroulante, sélectionnez le port WCF-Siebel que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **liaison** onglet et spécifier des valeurs pour les propriétés de liaison.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)