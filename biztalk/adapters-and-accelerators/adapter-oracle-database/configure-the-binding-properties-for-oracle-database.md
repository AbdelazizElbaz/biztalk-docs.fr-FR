---
title: "Configurer les propriétés de liaison pour la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding properties, specifying at run time
- binding properties, specifying at design time
ms.assetid: c59a1b5c-b52b-4161-82de-c4d89bfce5c7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73b7a5205b2fbfe0bc42bf5af0930356a003d5be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-binding-properties-for-oracle-database"></a>Configurer les propriétés de liaison pour la base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose plusieurs propriétés de liaison qui vous permettent de contrôler certaines de ses caractéristiques de comportement. Cette section fournit des informations sur la définition des propriétés de liaison à partir de Visual Studio et à partir de la console Administration de BizTalk Server. À partir de Visual Studio, vous devez spécifier les propriétés de liaison lors de la génération de schéma pour des opérations spécifiques. À partir de BizTalk Server, vous devez spécifier les propriétés de liaison dans le cadre de l’envoi ou le port de réception pour envoyer ou recevoir des messages à partir de la base de données Oracle.  
  
 Pour plus d’informations sur les propriétés de liaison, notamment une liste de propriétés de liaison pour [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
## <a name="specifying-binding-properties-from-visual-studio"></a>Spécification de propriétés de liaison à partir de Visual Studio  
 À partir de Visual Studio, vous devez spécifier les informations d’identification à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
#### <a name="to-specify-binding-properties-using-consume-adapter-service-add-in"></a>Pour spécifier les propriétés de liaison à l’aide de complément Consume Adapter Service  
  
1.  Avec le bouton droit de votre projet BizTalk, puis sélectionnez **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **oracleDBBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet et spécifier les propriétés de liaison différents.  
  
6.  Cliquez sur **OK**.  
  
#### <a name="to-specify-binding-properties-using-add-adapter-metadata-wizard"></a>Pour spécifier les propriétés de liaison à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur  
  
1.  Avec le bouton droit de votre projet BizTalk, puis sélectionnez **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
    |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
3.  Cliquez sur **Ajouter**. L’Assistant Ajout de métadonnées d’adaptateur s’ouvre.  
  
4.  Dans l’Assistant Ajout de métadonnées d’adaptateur, sélectionnez **WCF-OracleDB**. Sélectionnez l’ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] est installé et le nom de la base de données BizTalk.  
  
    > [!IMPORTANT]
    >  Si vous disposez déjà d’un port WCF-OracleDB configuré dans BizTalk, sélectionnez le port à partir de la **Port** liste.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** liste déroulante, sélectionnez **oracleDBBinding**, puis cliquez sur **configurer**.  
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet et spécifiez les valeurs de liaison, si elle existe, qui sont nécessaires avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous avez sélectionné un port d’envoi WCF-OracleDB existant, vous ne devez pas spécifier les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
8.  Cliquez sur **OK**.  
  
## <a name="specifying-binding-properties-from-the-biztalk-server-administration-console"></a>Spécification de propriétés de liaison à partir de la Console Administration de BizTalk Server  
 Dans la console Administration de BizTalk Server, vous devez spécifier les propriétés de liaison dans le cadre de la configuration du port WCF-Custom ou WCF-OracleDB.  
  
#### <a name="to-specify-binding-properties-for-the-wcf-custom-port"></a>Pour spécifier les propriétés de liaison pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
5.  À partir de la **Type de liaison** la liste déroulante, sélectionnez **oracleDBBinding**.  
  
6.  Dans le **Configuration** zone, spécifiez les valeurs pour les propriétés de liaison différente, cliquez sur **OK**.  
  
#### <a name="to-specify-binding-properties-for-the-wcf-oracledb-port"></a>Pour spécifier les propriétés de liaison pour le port WCF-OracleDB  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-OracleDB à la console Administration de BizTalk Server. Pour obtenir des instructions, consultez [Ajout de l’adaptateur de base de données Oracle à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-OracleDB que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **liaison** onglet et spécifier les valeurs des propriétés de liaison.  
  
    > [!NOTE]
    >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les propriétés de liaison liées notifications ne sont pas disponibles lors de la configuration d’un port d’envoi, car des notifications sont des opérations entrantes et nécessitent une configuration de port de réception.  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)