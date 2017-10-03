---
title: "Étape 2 (pour Azure) : Créer un accord EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8003697-4955-45c0-ba0b-e7c293a050a2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc2db7361aef663c70c7227febfea5fc08dc699a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-for-azure-create-an-edi-agreement"></a>Étape 2 (pour Azure) : Créer un accord EDI
Dans cette rubrique, vous allez créer des partenaires à l’aide du Portail Azure BizTalk disponible dans le cadre de [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]. Vous allez également créer un accord entre les deux partenaires (Northwind et Contoso) pour traiter le message de commande client X12 envoyé par Contoso à Northwind.  
  
### <a name="to-create-partners"></a>Pour créer des partenaires  
  
1.  À l’aide de votre compte Microsoft, connectez-vous au portail à [http://go.microsoft.com/fwlink/p/?LinkId=235056](http://go.microsoft.com/fwlink/p/?LinkId=235056).  
  
2.  Créez un partenaire pour Northwind. Suivez les étapes à [partenaires et les profils](http://msdn.microsoft.com/library/windowsazure/hh689791) pour créer un partenaire.  
  
    > [!IMPORTANT]
    >  Marquez ce partenaire comme étant le partenaire géré.  
  
3.  Répétez les étapes pour créer un partenaire pour Contoso. ***Ne le faites pas*** marquez ce partenaire comme étant un partenaire géré.  
  
### <a name="to-create-an-agreement"></a>Pour créer un accord  
  
1.  Dans la page accueil du portail, cliquez sur **accords**.  
  
2.  Sur le **accords** , cliquez sur le **X12** onglet si vous n’êtes pas déjà dans l’onglet. Puis cliquez sur **créer un accord**.  
  
3.  Dans le **nouvel accord** , entrez les informations suivantes :  
  
    |||  
    |-|-|  
    |**Field**|**Description**|  
    |Nom|Entrez le nom de l’accord. Pour ce didacticiel, spécifiez le nom de `DemoAgreement`.<br /><br /> **Remarque :** il s’agit d’un champ obligatoire. Le nom de l’accord doit être unique.|  
    | Description|Entrez des notes ou une description pour l’accord.|  
    |Profil du partenaire 1 (géré)|Sélectionnez le partenaire géré associé à l’accord. Un partenaire géré est un partenaire géré par le fournisseur de services, et les pipelines sont déployés pour ce partenaire lors du déploiement de l’accord. En général, les partenaires gérés par le fournisseur de services sont configurés comme étant des partenaires gérés, tandis que les partenaires de l’entreprise ne sont pas marqués comme étant des partenaires gérés.<br /><br /> **Remarque :** pour ce didacticiel, le partenaire géré est **Northwind**.<br /><br /> **Remarque :** le profil par défaut s’affiche dans le champ profil. Sélectionnez le profil voulu qui a été configuré pour le partenaire.|  
    |Profil du partenaire 2|Sélectionnez le partenaire associé à l’accord (qui n’est pas un partenaire géré).<br /><br /> **Remarque :** le profil par défaut s’affiche dans le champ profil. Sélectionnez le profil voulu qui a été configuré pour le partenaire.|  
  
     **Identités**  
  
    |**Field**|**Description**|  
    |---------------|---------------------|  
    |Qualificateur d’ID du partenaire 1|Sélectionnez un qualificateur d’authentification qui fournit des identités d’entreprise uniques aux partenaires commerciaux. Pour ce didacticiel, sélectionnez **ZZ-défini mutuellement**.|  
    |Valeur|Entrez `Northwind`.|  
    |Qualificateur d’ID de partenaire 2|Sélectionnez un qualificateur d’authentification qui fournit des identités d’entreprise uniques aux partenaires commerciaux. Pour ce didacticiel, sélectionnez **ZZ-défini mutuellement**.|  
    |Valeur|Entrez `Contoso`.|  
  
     **Suivi**  
  
    |**Field**|**Description**|  
    |---------------|---------------------|  
    |Suivre les propriétés de message au niveau de l’envoi|Activez cette option pour stocker les propriétés de message lors de l’envoi d’un message EDI au partenaire. Une fois enregistrées, vous pouvez interroger ces données en cliquant sur **suivi** dans le volet gauche sur le portail Azure BizTalk.<br /><br /> Lorsque activé, vous pouvez également stocker le corps du message en vérifiant **envoyer de suivre le corps du message côté**.|  
    |Suivre les propriétés de message au niveau de la réception|Activez cette option pour stocker les propriétés de message lors de la réception d’un message EDI en provenance d’un partenaire. Une fois enregistrées, vous pouvez interroger ces données en cliquant sur **suivi** dans le volet gauche sur le portail Azure BizTalk.<br /><br /> Lorsque activé, vous pouvez également stocker le corps du message en vérifiant **corps du message côté réception de suivi**.|  
  
4.  Cliquez sur **Continuer**.  
  
     En cliquant sur **continuer** ajoute deux nouveaux onglets, une pour les paramètres de réception et l’autre pour les paramètres d’envoi. Chaque onglet concerne un accord unidirectionnel entre les deux partenaires : un pour la réception des messages et l’autre pour l’envoi de messages.  
  
5.  Spécifiez les paramètres de réception.  
  
    1.  Sur le **Transport** , définissez le **type de Transport** sur HTTP.  
  
         Le **point de terminaison** champ affiche l’URL à laquelle Contoso doit envoyer le X12 message de commande client.  
  
    2.  Sur le **protocole** , spécifiez les valeurs suivantes.  
  
        1.  Le cas échéant, spécifiez des valeurs pour ISA1, ISA2, ISA3 et ISA4.  
  
        2.  Sous **accusés de réception**, sélectionnez **TA1 attendu** et **997 attendu** si vous souhaitez générer des accusés de réception techniques et fonctionnels en réponse pour la réception du Message.  
  
        3.  Sous **schémas**, cliquez sur le **télécharger** et téléchargez le **X12 schéma 840** (vous avez téléchargé à partir de [http://go.microsoft.com/fwlink/p/? LinkId = 235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)) et le **SalesOrder** schéma (vous avez créé dans [pour créer un schéma dans le projet EDI](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateSchema)).  
  
             Définissez les propriétés suivantes sous la **schémas** section.  
  
            |||  
            |-|-|  
            |Version|00401|  
            |Type de transaction (ST1)|840|  
            |schéma|/X12_00401_840.xsd|  
  
    3.  Sur le **transformer** page, téléchargez la transformation que vous avez créé dans [pour créer une transformation dans le projet EDI](../core/step-1-for-azure-create-the-edi-project.md#BKMK_CreateTrfm).  
  
         Sous **choisir les mappages que vous voulez exécuter en tant que partie de ce contrat**, choisissez **/x12_00401_840.xsd** pour **schémas** et **/EDI840TOSALESORDER. TRFM** pour **nom de fichier de transformation**.  
  
    4.  Sur le **itinéraire** page, sélectionnez **itinéraire vers la file d’attente du Bus de Service** et fournir l’adresse relative de la file d’attente à laquelle le message est envoyé. Pour ce didacticiel, spécifiez l’adresse relative `queueordersedi` afin que l’URL complète est `https://<namespace>.servicebus.appfabriclabs.com/queueordersedi`.  
  
        > [!NOTE]
        >  Ce didacticiel ne couvre pas le scénario au cours duquel un message ayant échoué est envoyé au point de terminaison que vous spécifiez dans les paramètres de suspension de message. Toutefois, pour la réussite du déploiement de l’accord, vous devez indiquer une valeur pour ce paramètre. Vous pouvez entrer une valeur non vide.  
  
6.  Spécifiez les paramètres d’envoi.  
  
    > [!NOTE]
    >  Pour les besoins du scénario décrit dans le cadre de ce didacticiel, vous n’avez pas besoin de configuration côté envoi pour l’accord. Toutefois, un accord ne peut pas être déployé si vous ne spécifiez pas de paramètres d’envoi, même s’il s’agit de valeurs factices. En outre, sur le **paramètres d’envoi** onglet, vous n’avez pas besoin de fournir de valeurs factices pour **URI entrant**, **transformer**, et **le traitement par lot**.  
  
    1.  Sur le **protocole** sous **schémas**, cliquez sur le **télécharger** et téléchargez le schéma pour le X12 message 840.  
  
         Définir le **Version** à **00401**, **Type de Transaction** à **840**, et **schéma** à  **X12_00401_840**.  
  
    2.  Sur le **Transport** , spécifiez les points de terminaison où les messages de réponse ou les accusés de réception seront envoyés aux partenaires. Vous devez spécifier un point de terminaison pour chaque message traité avec succès, ainsi que pour chaque message interrompu en raison d’une erreur de traitement.  
  
7.  Cliquez sur **déployer le contrat** pour déployer l’accord. L’accord est maintenant déployé à l’URL affichée dans le **Transport** page de la **paramètres de réception** onglet.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)