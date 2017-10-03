---
title: "Configurer les propriétés de liaison pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfdca8c8-4434-4a9f-8e2a-970988c2f685
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddb414ae80e7cff6717d232d1734ec8b98cd2006
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-binding-properties-for-oracle-e-business-suite"></a>Configurer les propriétés de liaison pour Oracle E-Business Suite
Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]expose plusieurs propriétés de liaison qui vous permettent de contrôler certaines de ses caractéristiques de comportement. Cette section fournit des informations sur la définition des propriétés de liaison à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier les propriétés de liaison lors de la génération de schéma pour des opérations spécifiques. À partir de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez spécifier les propriétés de liaison dans le cadre de l’envoi ou port de réception pour envoyer ou recevoir des messages à partir d’Oracle E-Business Suite.  
  
 Pour plus d’informations sur les propriétés de liaison, notamment une liste de propriétés de liaison pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## <a name="specifying-binding-properties-from-visual-studio"></a>Spécification de propriétés de liaison à partir de Visual Studio  
 À partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez spécifier les propriétés de liaison à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  
  
#### <a name="to-specify-binding-properties-using-consume-adapter-service-add-in"></a>Pour spécifier les propriétés de liaison à l’aide de complément Consume Adapter Service  
  
1.  Avec le bouton droit de votre projet BizTalk, puis **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **Consume Adapter Service**.|  
    |**Modèles**|Cliquez sur **Consume Adapter Service**.|  
  
3.  Pour démarrer le **Consume Adapter Service** boîte de dialogue, cliquez sur **ajouter**.  
  
4.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **oracleEBSBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet, puis spécifiez les propriétés de liaison différents.  
  
6.  Cliquez sur **OK**.  
  
#### <a name="to-specify-binding-properties-using-add-adapter-metadata-wizard"></a>Pour spécifier les propriétés de liaison à l’aide d’Assistant Ajouter les métadonnées de l’adaptateur  
  
1.  Avec le bouton droit de votre projet BizTalk, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Catégories**|Cliquez sur **ajouter l’adaptateur**.|  
    |**Modèles**|Cliquez sur **ajouter les métadonnées de l’adaptateur**.|  
  
3.  Cliquez sur **Ajouter**. Le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] s’ouvre.  
  
4.  Dans le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], sélectionnez **WCF-OracleEBS**. Sélectionnez l’ordinateur sur lequel BizTalk Server est installé et le nom de la base de données BizTalk.  
  
    > [!IMPORTANT]
    >  Si vous disposez déjà d’un port WCF-OracleEBS configuré dans BizTalk Server, sélectionnez le port dans la liste des ports.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans le **Consume Adapter Service** boîte de dialogue, à partir de la **sélectionner une liaison** , sélectionnez **oracleEBSBinding**, puis cliquez sur **configurer**.  
  
7.  Cliquez sur le **propriétés de liaison** onglet et spécifiez les valeurs de liaison, si elle existe, qui sont nécessaires avant de générer le schéma. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
    > [!NOTE]
    >  Si vous avez sélectionné un existant port d’envoi WCF-OracleEBS, vous ne spécifiez ne pas les propriétés de liaison. Les propriétés de liaison sont récupérées à partir de la configuration du port d’envoi. Toutefois, vous pouvez choisir de spécifier les propriétés de liaison qui sont nécessaires au moment du design, le cas échéant. Dans ce cas, les nouvelles valeurs des propriétés de liaison seront utilisées au moment du design lors de la génération de métadonnées. Toutefois, au moment de l’exécution les valeurs spécifiées pour les propriétés de liaison dans la configuration du port d’envoi sera appliquées.  
  
8.  Cliquez sur **OK**.  
  
## <a name="specifying-binding-properties-from-the-biztalk-server-administration-console"></a>Spécification de propriétés de liaison à partir de la Console Administration de BizTalk Server  
 À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration, vous devez spécifier les propriétés de liaison dans le cadre de la configuration du port WCF-Custom ou WCF-OracleEBS.  
  
#### <a name="to-specify-binding-properties-for-the-wcf-custom-port"></a>Pour spécifier les propriétés de liaison pour le port WCF-Custom  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
3.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
5.  À partir de la **Type de liaison** liste, sélectionnez **oracleEBSBinding**.  
  
6.  Dans le **Configuration** zone, spécifiez les valeurs pour les propriétés de liaison différente, puis cliquez sur **OK**.  
  
#### <a name="to-specify-binding-properties-for-the-wcf-oracleebs-port"></a>Pour spécifier les propriétés de liaison pour le port WCF-OracleEBS  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Ajouter l’adaptateur WCF-OracleEBS à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions, consultez [Ajout de l’adaptateur Oracle E-Business Suite à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).  
  
3.  Dans l’arborescence de la console, développez **groupe BizTalk**, puis développez **Applications**, puis développez l’application sous lequel vous souhaitez créer un port, puis cliquez sur **Ports d’envoi** ou **Ports de réception**. Dans le volet droit, vous pouvez choisir de créer un port ou de sélectionner un port existant.  
  
4.  Dans la boîte de dialogue Propriétés du port, à partir de la **Type** la liste déroulante, sélectionnez l’adaptateur WCF-OracleEBS que vous avez ajouté précédemment, puis cliquez sur **configurer**.  
  
    > [!NOTE]
    >  Pour afficher la boîte de dialogue de propriétés emplacement pour un port de réception, cliquez sur le **un emplacement de réception** onglet dans le volet gauche de la boîte de dialogue des propriétés de port, puis cliquez sur **nouveau**.  
  
5.  Dans la boîte de dialogue Propriétés du transport, cliquez sur le **liaison** onglet et spécifier les valeurs des propriétés de liaison.  
  
    > [!NOTE]
    >  Les propriétés de liaison sont affichées selon que vous configurez un port d’envoi ou un port de réception. Par exemple, les propriétés de liaison liées notifications ne sont pas disponibles lors de la configuration d’un port d’envoi, car des notifications sont des opérations entrantes et nécessitent une configuration de port de réception.  
  
## <a name="see-also"></a>Voir aussi  
 [Blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)