---
title: "Étape 5 (locaux) : Générer le schéma pour l’insertion d’un Message dans la SalesOrder Table | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab0bc1a7-8bcd-4110-88e6-4eddf0b57068
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: facb5d638ed82e1632e434a2a9c9063a2c3daa68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-on-premises-generate-the-schema-for-inserting-a-message-inito-salesorder-table"></a>Étape 5 (locaux) : Générer le schéma pour l’insertion d’un Message dans la SalesOrder Table
Selon le scénario d’entreprise, le message de commande envoyé par Contoso de X12 doivent être insérés dans de Northwind **SalesOrder** table si la quantité commandée est supérieure à 100. Pour insérer un message dans un **SalesOrder** table, vous devez générer le schéma pour le **insérer** opération sur la table. Dans cette rubrique, vous allez créer un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution, puis utiliser le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] pour générer le schéma pour effectuer une **insérer** opération sur le **SalesOrder** table.  
  
### <a name="to-generate-the-schema-for-insert-operation-on-salesorder-table"></a>Pour générer le schéma pour l’opération Insert sur la table SalesOrder  
  
1.  Créez un projet Visual Studio [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. À partir de Visual Studio **fichier** menu, cliquez sur **nouveau**, puis cliquez sur **projet**. Dans le **nouveau projet** boîte de dialogue, dans la liste des modèles installés, cliquez sur **projets BizTalk**, puis sélectionnez **vide [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet**. Entrez le nom du projet `OrderProcessingDemo` puis cliquez sur **OK**.  
  
2.  Cliquez sur le nom du projet dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
3.  Dans le **ajouter les éléments générés** boîte de dialogue, sélectionnez **Consume Adapter Service**, puis cliquez sur **ajouter**. Le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] s’ouvre.  
  
4.  À partir de la **sélectionner une liaison** la liste déroulante, sélectionnez **sqlBinding**, puis cliquez sur **configurer**.  
  
5.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet et à partir de la **type d’informations d’identification du Client** liste déroulante, effectuez l’une des opérations suivantes :  
  
    |Cliquez sur ce bouton|Pour effectuer cette opération|  
    |----------------|----------------|  
    |**Aucun**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Windows**|Se connecter à SQL Server à l’aide de l’authentification Windows.|  
    |**Nom d’utilisateur**|Spécifier le nom d’utilisateur et le mot de passe pour vous connecter à SQL Server en spécifiant des informations d’identification pour un utilisateur défini dans une base de données SQL Server. Notez que le nom d’utilisateur et le mot de passe respectent la casse. **Remarque :** si vous laissez le **nom d’utilisateur** et **mot de passe** champs, l’adaptateur se connecte à SQL Server à l’aide de l’authentification Windows.|  
  
6.  Cliquez sur le **propriétés URI** onglet et spécifiez des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], consultez [URI de connexion SQL Server](http://msdn.microsoft.com/library/dd788089.aspx).  
  
    > [!NOTE]
    >  Si les paramètres de connexion contiennent des caractères réservés, vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Toutefois, si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
    > [!NOTE]
    >  Si vous ne spécifiez aucune valeur sous l’onglet Propriété de l’URI, le [!INCLUDE[consumeadapterservshort](../includes/consumeadapterservshort-md.md)] utilise l’URI `mssql://.//`. Dans ce cas, l’adaptateur se connecte à la base de données par défaut et à l’instance de base de données par défaut sur l’ordinateur local.  
  
7.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur **OK**. Dans le **Consume Adapter Service** boîte de dialogue, cliquez sur **connexion**.  
  
8.  À partir de la **sélectionner une catégorie** , développez **Tables**, puis cliquez sur le **SalesOrder** table.  
  
9. À partir de la **catégories et opérations disponibles** boîte, sélectionnez **insérer**, cliquez sur **ajouter**, puis cliquez sur **OK**. Cette action a pour effet d’ajouter de nouveaux éléments à l’Explorateur de solutions. Le fichier de schéma (**TableOperation.dbo.SalesOrder.xsd**) est le schéma généré pour effectuer une opération d’insertion sur la **SalesOrder** table.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)