---
title: "Étape 2 : Configurer le système Salesforce | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a4b09fb-70a7-4eec-b1e3-f05de0e84df1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d65a1c741103b9c8f1e9493b7bd2aa56eef8cf18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-set-up-the-salesforce-system"></a>Étape 2 : Configurer le système Salesforce
Au cours de cette étape, vous allez configurer Salesforce pour envoyer des notifications lorsqu'une opportunité est clôturée avec succès. Avant de pouvoir envoyer des notifications, vous devez effectuer les étapes suivantes :  
  
-   Créer un compte dans Salesforce. Un compte représente un client pour Northwind.  
  
-   Créer une opportunité pour le compte. Une opportunité représente une opportunité de vente potentielle au client. Dans le cadre de l'opportunité, vous pouvez également ajouter des détails sur le produit qui intéresse le client.  
  
-   Créer un workflow dans Salesforce.  
  
-   Créer une définition d'application connectée Salesforce.  
  
> [!NOTE]
>  Les étapes de cette rubrique supposent que vous possédez déjà un compte de développeur Salesforce. Pour créer un nouveau compte de développeur dans Salesforce, accédez à [http://go.microsoft.com/fwlink/?LinkId=296424](http://go.microsoft.com/fwlink/?LinkId=296424).  
  
### <a name="to-create-an-account-in-salesforce"></a>Pour créer un compte dans Salesforce  
  
1.  Connectez-vous au portail Salesforce.com à l'aide de vos informations d'identification développeur.  
  
2.  Dans le portail, cliquez sur le **comptes** onglet, puis cliquez sur **nouveau**.  
  
3.  Sur le **nouveau compte** , fournissez des valeurs pour les différents champs. En spécifiant une valeur pour **nom de compte** est obligatoire. Pour ce didacticiel, spécifiez le nom du compte en tant que `Customer1`.  
  
4.  Cliquez sur **Enregistrer**.  
  
### <a name="to-create-an-opportunity-for-the-customer"></a>Pour créer une opportunité pour le client  
  
1.  Dans le portail Salesforce.com, cliquez sur le **opportunités** onglet.  
  
2.  Dans le **opportunités récentes** , cliquez sur **nouveau**.  
  
3.  Dans la page Nouvelle opportunité, spécifiez les valeurs suivantes :  
  
    1.  Spécifiez un **nom d’opportunité**, par exemple, `Opportunity with Customer 1`.  
  
    2.  Spécifiez le **nom de compte**. Cette valeur représente le compte auquel cette opportunité est associée. Pour ce didacticiel, définissez le compte `Customer1`. Vous avez créé ce compte lors de la procédure précédente.  
  
    3.  Spécifiez un **Date de clôture**. Il s'agit de la date à laquelle l'opportunité doit être clôturée.  
  
    4.  Spécifiez un **étape**. Il s'agit du stade actuel de l'opportunité. Pour commencer, vous pouvez définir la possibilité d’une autre manière, par exemple, **nécessite une analyse**.  
  
         ![Créer une opportunité dans Salesforce](../core/media/bts-sf-create-opp.jpg "BTS_SF_Create_Opp")  
  
        > [!NOTE]
        >  Assurez-vous que vous ne définissez pas l’étape **fermées/gagnées** pour commencer. Pour le scénario de ce didacticiel, chaque fois que l’étape est définie sur **fermées/gagnées** une notification est envoyée à un point de terminaison de relais [!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)]. Nous n’avons pas cette partie de la solution encore configuré, vous devez donc pas affecter l’étape **fermées/gagnées**.  
  
    5.  Spécifiez des valeurs pour les autres champs facultatifs, puis cliquez **enregistrer**.  
  
    6.  Sur la page opportunité de Customer1, sous le **produits** , cliquez sur **ajouter un produit**.  
  
    7.  Dans la liste de produits, sélectionnez les produits que le client s’intéresse, puis cliquez sur **sélectionnez**.  
  
    8.  Pour chaque produit sélectionné, spécifiez une quantité voulue par le client, puis cliquez sur **enregistrer**.  
  
         ![Ajouter des produits à une opportunité](../core/media/bts-sf-add-product.gif "BTS_SF_Add_Product")  
  
## <a name="create-a-salesforce-workflow"></a>Créer un workflow Salesforce  
 Dans cette étape, nous créons un workflow pour envoyer une notification chaque fois qu'une opportunité est clôturée avec succès. La notification est sous la forme d’un message SOAP et est envoyée à un point de terminaison de relais hébergé sur [!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)].  
  
#### <a name="to-create-a-workflow-for-opportunities"></a>Pour créer un workflow pour les opportunités  
  
1.  Dans le portail Salesforce, cliquez sur votre nom de connexion à l’angle supérieur droit de la page, puis cliquez sur **le programme d’installation**.  
  
2.  Dans le volet gauche, sous **programme d’installation de l’application**, développez **créer**, développez **Workflow & approbations**, puis cliquez sur **les règles de flux de travail**.  
  
    > [!NOTE]
    >  Si vous ouvrez la page Règles de workflow pour la première fois, le système vous présente des informations pour vous permettre de comprendre comment fonctionnent les workflows dans Salesforce. Lisez les informations, puis **continuer**.  
  
3.  Sur le **toutes les règles de flux de travail** , cliquez sur **nouvelle règle**.  
  
4.  À partir de la **sélectionner un objet** , cliquez sur **opportunité**, puis cliquez sur **suivant**.  
  
5.  Dans la page suivante, spécifiez ce qui suit :  
  
    1.  Définir le **nom de règle** comme `Closed Opportunity`.  
  
    2.  Définir le **les critères d’évaluation** en tant que **créé et chaque fois qu’il est modifié pour répondre ensuite aux critères**.  
  
    3.  Pour le **critères de règles**, configuré pour s’exécuter la règle lorsque le **critères**.  
  
    4.  Définissez **champ** à **opportunité : étape**, **opérateur** à **est égal à**, et **valeur** à `Closed Won`.  
  
         ![Créer un workflow Salesforce](../core/media/bts-sf-create-workflow.jpg "BTS_SF_Create_Workflow")  
  
    5.  Cliquez sur **enregistrer et suivant**.  
  
6.  Définissez l'action de workflow pour la nouvelle règle :  
  
    1.  Sur le **spécifier des Actions de flux de travail** , cliquez sur **ajouter une Action de flux de travail** puis cliquez sur **nouveau Message sortant**.  
  
    2.  Définir le **nom** et **nom Unique** champs à `NewOp1`.  
  
    3.  Spécifiez une description, tels que le `Message sent when an opportunity is successfully closed`.  
  
    4.  Spécifiez le **URL de point de terminaison** comme `https://btssalesforce.servicebus.windows.net/notifications/opportunity`.  
  
         Ici, **btssalesforce** est votre [!INCLUDE[sb](../includes/sb-md.md)] espace de noms que vous avez créé précédemment. **/notifications/opportunity/** représente le relais que nous allons créer dans les étapes ultérieures de ce didacticiel.  
  
        > [!NOTE]
        >  Vous devez spécifier l'espace de noms [!INCLUDE[sb](../includes/sb-md.md)] que vous avez créé précédemment.  
  
    5.  Assurez-vous que le **composant protégé** case à cocher est désactivée et la **envoyer un ID de Session** case à cocher est activée.  
  
    6.  Pour **opportunité aux champs pour envoyer** sélectionner à partir de la **champs disponibles** liste, puis cliquez sur le **ajouter** bouton.  
  
    7.  Cliquez sur **enregistrer** puis cliquez sur **fait**.  
  
    8.  Dans le volet gauche, sous **programme d’installation de l’application**, développez **créer**, développez **Workflow & approbations**, puis cliquez sur **les règles de flux de travail**. Vérifiez que le **opportunité fermée** règle y sont répertoriée. Sous le **Action** colonne pour le **opportunité fermée** de règles, cliquez sur **activer** pour activer la règle.  
  
## <a name="create-a-salesforce-connected-application"></a>Créer une application connectée Salesforce  
 La création d'une définition d'application connectée génère un jeu de clés nécessaires pour demander des jetons OAuth pour accéder à la connexion à Salesforce. Dans les phases ultérieures de ce didacticiel, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sera l'application connectée qui servira à interroger Salesforce à l'aide de la définition d'application connectée.  
  
#### <a name="to-create-a-connected-application-for-salesforce"></a>Pour créer une application connectée pour Salesforce  
  
1.  Dans le portail Salesforce, cliquez sur votre nom de connexion à l’angle supérieur droit de la page, puis cliquez sur **le programme d’installation**.  
  
2.  Dans le volet gauche, sous **programme d’installation de l’application**, développez **créer**, puis développez **applications**. Sur le **applications** sous le **applications connectées** , cliquez sur **nouveau**.  
  
3.  Dans le **nouvelle application de connexion** , spécifiez les éléments suivants :  
  
    1.  Pour **nom d’application connectée**, spécifiez `BizTalk_Salesforce`.  
  
    2.  Pour **nom du développeur**, spécifier votre journal sur le nom.  
  
    3.  Pour **messagerie du Contact**, spécifiez votre adresse de messagerie.  
  
    4.  Pour **URL de rappel**, spécifiez une URL valide.  
  
        > [!NOTE]
        >  Compte tenu de la façon dont nous nous authentifions auprès de Salesforce dans ce scénario, la valeur que vous indiquez ici n'est pas utilisée.  
  
    5.  Sous **portées OAuth disponibles**, sélectionnez **accès complet**, **effectue des demandes à votre place à tout moment**, et **accès et de gérer vos données**puis cliquez sur le **ajouter** bouton pour les déplacer vers le **portées OAuth sélectionnées**.  
  
    6.  Cliquez sur **Enregistrer**. La page qui apparaît contient des informations sur la **clé de consommateur** et **Secret de consommateur**. Vous devez prendre note de ces valeurs. Vous en aurez besoin lors de la connexion à Salesforce à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
         ![Touches d’accès de la force de vente](../core/media/bts-sf-consumer-keys.jpg "BTS_SF_Consumer_Keys")  
  
4.  Enfin, générez un jeton de sécurité requis pour la connexion à Salesforce à partir de sites réseau inconnus.  
  
    1.  Dans le volet gauche du portail Salesforce, sous **configuration personnel**, développez **personnelles**, puis cliquez sur **Reset My Security Token**.  
  
    2.  Lisez l’avertissement, puis cliquez sur **Reset Security Token**.  
  
    3.  Vous devriez recevoir le jeton de sécurité à l'adresse e-mail que vous avez spécifiée lors de la création de votre compte Salesforce.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 6 : Intégration de BizTalk Server 2013 avec Salesforce](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)