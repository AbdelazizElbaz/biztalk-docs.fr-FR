---
title: "Configurer les propriétés de liaison de l’adaptateur SAP | Documents Microsoft"
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
ms.assetid: 259a5895-c19d-409c-b2fc-bfdf59d5d74b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a16a95818ed4d63fd97b9fca1f9ea86ebd14de80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-binding-properties-for-the-sap-adapter"></a>Configurer les propriétés de liaison de l’adaptateur SAP
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose plusieurs propriétés de liaison qui vous permettent de contrôler certaines de ses caractéristiques de comportement. Cette section fournit des informations sur la définition des propriétés de liaison à partir de Visual Studio (conception) et de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration (temps d’exécution). Au moment du design, vous devez spécifier les propriétés de liaison pour générer le schéma pour des opérations spécifiques. Au moment de l’exécution, vous devez spécifier les propriétés de liaison dans le cadre de l’envoi ou le port de réception pour envoyer ou recevoir des messages à partir du système SAP.  
  
 Pour plus d’informations sur les propriétés de liaison, notamment une liste de propriétés de liaison pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
## <a name="enter-binding-properties-at-design-time"></a>Entrez les propriétés de liaison au moment du Design  
 Pour le moment du design, vous pouvez spécifier les propriétés de liaison à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
### <a name="enter-binding-properties-using-consume-adapter-service-add-in"></a>Entrez les propriétés de liaison à l’aide de complément Consume Adapter Service  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **sapBinding**, puis cliquez sur **configurer** .  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet, puis spécifiez les propriétés de liaison différents.  
  
6.  Cliquez sur **OK**.  
  
### <a name="enter-binding-properties-using-add-adapter-metadata-wizard"></a>Entrez les propriétés de liaison à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
    |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
3.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
4.  Dans l’Assistant Ajout d’adaptateur, sélectionnez **WCF SAP**. Sélectionnez l’ordinateur sur lequel BizTalk Server est installé et le nom de la base de données BizTalk.  
  
    > [!IMPORTANT]
    >  Si vous disposez déjà d’un port WCF SAP configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **sapBinding**, puis cliquez sur **configurer** .  
  
7.  Cliquez sur le **propriétés de liaison** onglet et spécifier les valeurs de liaison, si elle existe, qui sont nécessaires pour être spécifié avant de générer le schéma. Par exemple, vous devez spécifier une valeur pour le **GenerateFlatFileCompatibleIDoc** avant la génération de schéma pour recevoir des IDOC à partir d’un système SAP. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous avez sélectionné un port d’envoi WCF-SAP existant, vous ne devez pas spécifier les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
8.  Cliquez sur **OK**.  
  
## <a name="enter-binding-properties-at-run-time"></a>Entrez les propriétés de liaison au moment de l’exécution  
 Temps d’exécution, vous pouvez spécifier les propriétés de liaison du port WCF-Custom ou la configuration de WCF-SAP dans le cadre du [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
### <a name="enter-binding-properties-for-the-wcf-custom-port"></a>Entrez les propriétés de liaison de port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans le **propriétés de Port** boîte de dialogue, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
5.  À partir de la **Type de liaison** la liste déroulante, sélectionnez **sapBinding**.  
  
6.  Dans le **Configuration** zone, spécifiez les valeurs pour les propriétés de liaison différente, puis cliquez sur **OK**.  
  
### <a name="enter-binging-properties-for-the-wcf-sap-port"></a>Entrez les propriétés de liaison de port WCF SAP  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-SAP pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-SAP que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **liaison** onglet et spécifier les valeurs des propriétés de liaison.  
  
    > [!NOTE]
    >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les opérations associées à des messages de propriétés de liaison ne sont pas disponibles lors de la configuration d’un port d’envoi, car les opérations entrantes nécessitent une configuration de port de réception.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)