---
title: "Procédure pas à pas : Module 2 - intégration d’Office avec Windows SharePoint Services adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows SharePoint Services adapters, InfoPath forms
- InfoPath forms, creating
- InfoPath forms, Windows SharePoint Services adapters
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapter tutorials, integrating Microsoft Office
- Windows SharePoint Services, document libraries
ms.assetid: 2f81a712-bb20-4c32-bbac-fb438deded38
caps.latest.revision: "48"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64e23cef8b362accba726c60945548a3345c9c45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-module-2---integrating-office-with-the-windows-sharepoint-services-adapter"></a>Procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services
Cette procédure pas à pas est la suite de [procédure pas à pas : Module 1 - envoi et réception de Messages avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) et vous montre comment intégrer Microsoft Office à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en fonction du contenu application de routage (CBR) vous avez créé. Pour une présentation de l’adaptateur Windows SharePoint Services, consultez [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez avoir un déploiement sur un seul serveur avec une installation complète de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Vous devez effectuer la procédure suivante : [procédure pas à pas : Module 1 - envoi et réception de Messages avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md)  
  
 Pour plus d’informations sur l’utilisation de l’adaptateur Windows SharePoint Services dans un déploiement multiserveur, consultez [configuration et déploiement de l’adaptateur Windows SharePoint Services](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).  
  
## <a name="create-a-biztalk-project"></a>Création d'un projet BizTalk  
 Cette procédure permet de créer un projet BizTalk vide et un schéma à l'aide de l'Éditeur BizTalk. Elle est requise pour créer le schéma du formulaire InfoPath qui sera utilisé ultérieurement.  
  
#### <a name="create-a-strong-name-key-file"></a>Pour créer un fichier de clé de nom fort  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  Type `sn -k C:\WSSAdapterWalkthrough\OrderProcess.snk`, puis appuyez sur **entrée**. La paire de clés est alors écrite.  
  
3.  Fermez l'invite de commande.  
  
#### <a name="create-an-empty-biztalk-project"></a>Créer un projet BizTalk vide  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Cliquez sur **fichier**, **nouveau**, puis cliquez sur **projet**.  
  
3.  Sous **types de projet**, sélectionnez **projets BizTalk**.  
  
4.  Sous **modèles**, sélectionnez **projet BizTalk Server vide**.  
  
5.  Type `OrderProcess` dans les **nom** champ.  
  
6.  Tapez le chemin d’accès de fichier dans votre répertoire de travail dans le **emplacement** champ. Par exemple, `C:\WSSAdapterWalkthrough\`.  
  
7.  Cliquez sur **OK**.  
  
#### <a name="associate-the-key-file-with-the-assembly"></a>Pour associer le fichier de clé à l'assembly  
  
1.  Dans l’Explorateur de solutions, cliquez sur le `OrderProcess` de projet, puis cliquez sur **propriétés** pour lancer le Concepteur de projet.  
  
2.  Cliquez sur l'onglet **Signature** .  
  
3.  Sélectionnez l'option **Signer l'assembly** , cliquez sur l'option **Choisir un fichier de clé de nom fort** dans la liste déroulante, puis sur **Parcourir**.  
  
4.  Tapez `C:\WSSAdapterWalkthrough\OrderProcess.snk`.  
  
5.  Cliquez sur **Ouvrir**.  
  
#### <a name="create-an-xsd-schema-by-using-the-biztalk-editor"></a>Pour créer un schéma XSD à l'aide de l'Éditeur BizTalk  
  
1.  Dans l’Explorateur de solutions, cliquez sur le `OrderProcess` de projet, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Sous **catégories**, cliquez sur **les fichiers de schéma**.  
  
3.  Sous **modèles**, cliquez sur **schéma**.  
  
4.  Type `OrderProcessSchema` dans les **nom** champ, puis cliquez sur **ajouter**.  
  
5.  Dans la fenêtre Propriétés pour `OrderProcessSchema`, sélectionnez `Qualified` pour le **Element FormDefault** propriété.  
  
6.  Dans la fenêtre Propriétés pour `OrderProcessSchema`, type `http://OrderProcess.PurchaseOrder` dans les **cible Namespace** champ.  
  
7.  Dans le **l’Éditeur BizTalk**, avec le bouton droit `Root`, cliquez sur **renommer**, puis tapez `PurchaseOrder`.  
  
8.  Cliquez sur le **PurchaseOrder** nœud, cliquez sur **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.  
  
9. Nommez-le `PurchaseOrderID`.  
  
10. Créez un autre élément de champ enfant et nommez-le `BillTo`.  
  
11. Créez un autre élément de champ enfant et nommez-le `Amount`.  
  
12. Dans la fenêtre Propriétés, définissez la **Type de données** propriété `Amount` à xs : unsignedInt.  
  
13. Créez un autre élément de champ enfant et nommez-le `PurchaseOrderDate`.  
  
14. Dans la fenêtre Propriétés, définissez la **Type de données** propriété `PurchaseOrderDate` à xs : DateTime.  
  
15. Cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.  
  
16. Fermez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="create-an-infopath-form"></a>Création d'un formulaire InfoPath  
 Cette procédure permet de créer une autre bibliothèque de documents et un formulaire InfoPath à partir du schéma créé dans la procédure précédente. Ce formulaire InfoPath sera utilisé pour envoyer un document à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Cette procédure pas à pas requiert Microsoft Office InfoPath 2007.  
  
#### <a name="create-a-new-document-library"></a>Pour créer une bibliothèque de documents  
  
1.  Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  Dans la barre de navigation supérieure, cliquez sur **créer**.  
  
3.  Sous **bibliothèques de documents**, cliquez sur **bibliothèque de documents**.  
  
4.  Dans le **nom et Description** , tapez `InfoPathSolutions` dans les **champ nom**.  
  
5.  Dans le **Navigation** section, sélectionnez **Oui** pour afficher cette bibliothèque de formulaires dans la barre de lancement rapide.  
  
6.  Dans le **modèle de Document** section, sélectionnez `None` pour le **modèle de Document**.  
  
7.  Cliquez sur **Créer**. Vous êtes alors redirigé vers la bibliothèque vide que vous venez de créer.  
  
8.  Sur le côté gauche, cliquez sur **modifier les paramètres et les colonnes**.  
  
9. Sous **colonnes**, cliquez sur **ajouter une nouvelle colonne**.  
  
10. Sous **nom et le Type**, type `Namespace` dans les **nom** champ.  
  
11. Cliquez sur **OK**.  
  
12. Fermez le site Web `WSSAdapterWalkthrough`.  
  
#### <a name="create-an-infopath-form-based-on-the-orderprocessschema-schema-file"></a>Pour créer un formulaire InfoPath à partir du fichier de schéma OrderProcessSchema  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office InfoPath 2007**.  
  
2.  Dans le **remplir un formulaire** boîte de dialogue, sélectionnez **concevoir un formulaire.**  
  
3.  Dans le **concevoir un formulaire** volet des tâches, sélectionnez **nouveau à partir de Document ou schéma XML**.  
  
4.  Dans le **Assistant Source de données**, cliquez sur **Parcourir** et sélectionnez le fichier de schéma que vous avez créé dans la dernière procédure. Par exemple, `C:\WSSAdapterWalkthrough\OrderProcess\OrderProcess\OrderProcessSchema.xsd`.  
  
5.  Cliquez sur **Suivant**, puis sur **Terminer**.  
  
6.  Dans le **Source de données** volet de tâches, cliquez sur le **PurchaseOrder** nœud, puis cliquez sur **Section avec contrôles**. Cette opération crée le formulaire à partir du modèle.  
  
7.  Cliquez sur **fichier**, cliquez sur **enregistrer**, puis cliquez sur **enregistrer**.  
  
8.  Dans le **enregistrer en tant que** boîte de dialogue, tapez `PurchaseOrder.xsn` dans les **nom de fichier** champ, puis cliquez sur **enregistrer**.  
  
9. Cliquez sur **fichier**, puis cliquez sur **publier**.  
  
10. Dans le **l’Assistant Publication de**, cliquez sur **suivant**.  
  
11. Sélectionnez **vers un serveur Web**, puis cliquez sur **suivant**.  
  
12. Tapez le chemin d’accès et le nom de fichier à votre `InfoPathSolutions` bibliothèque de documents, puis cliquez sur **suivant**. Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough/InfoPathSolutions/PurchaseOrder.xsn`.  
  
13. Cliquez sur **Terminer**, puis cliquez sur **fermer**.  
  
14. Fermez Microsoft InfoPath.  
  
## <a name="modify-the-sharepoint-document-libraries"></a>Modification des bibliothèques de documents SharePoint  
 Cette procédure permet de mettre à jour la propriété d'espace de noms pour le fichier PurchaseOrder.xsn et de modifier la bibliothèque de documents de destination. Cet espace de noms sert de variable lors de l'identification des abonnés aux documents publiés pour les scénarios de routage basé sur le contenu.  
  
#### <a name="update-the-namespace-for-purchaseorderxsn"></a>Pour mettre à jour l'espace de noms pour PurchaseOrder.xsn  
  
1.  Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  Sur le côté gauche, sous **Documents**, cliquez sur `InfoPathSolutions`.  
  
3.  Déplacez le pointeur sur `PurchaseOrder.xsn`, faites un clic droit, puis cliquez sur **modifier les propriétés de**.  
  
4.  Type `http://OrderProcess.PurchaseOrder` dans les **Namespace** champ, puis cliquez sur **enregistrer et fermer**.  
  
#### <a name="modify-the-destination-document-library"></a>Pour modifier la bibliothèque de documents de destination  
  
1.  Dans la barre de navigation supérieure, cliquez sur **Documents et listes**.  
  
2.  Sous **bibliothèques de documents**, cliquez sur **Destination**.  
  
3.  Sur le côté gauche, cliquez sur **modifier les paramètres et les colonnes**.  
  
4.  Sous **colonnes**, cliquez sur **ajouter une nouvelle colonne**.  
  
5.  Sous **nom et le Type**, type `Partner Name` dans les **nom de la colonne** champ.  
  
6.  Cliquez sur **OK**.  
  
7.  Fermez le site Web `WSSAdapterWalkthrough`.  
  
## <a name="modify-the-send-port-from-walkthrough-1"></a>Modification du port d'envoi à partir de la procédure pas à pas 1  
 Cette procédure permet de modifier le port d'envoi à partir de la procédure pas à pas 1. Elle est requise pour garantir l'acheminement correct vers le port d'envoi du document traité dans cette procédure pas à pas.  
  
#### <a name="modify-the-send-port"></a>Modification du port d'envoi  
  
1.  Ouvrez **Administration de BizTalk Server.**  
  
2.  Développez **Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur le **Ports d’envoi** nœud.  
  
3.  Avec le bouton droit `SendToDestination`, puis cliquez sur **propriétés**.  
  
4.  Sous **Transport**, cliquez sur **configurer**.  
  
5.  Dans le **nom de fichier** , tapez `PurchaseOrder2-%XPATH=//pons:PurchaseOrder/pons:PurchaseOrderID%.xml`.  
  
6.  Dans le **Namespace alias** , tapez `pons="http://OrderProcess.PurchaseOrder"`.  
  
7.  Dans le **bibliothèque de documents modèles**, type `InfoPathSolutions`.  
  
8.  Dans le **modèles Namespace colonne**, type `Namespace`.  
  
9. Sélectionnez `Yes` pour le **intégration de Microsoft Office** propriété.  
  
10. Sous **l’intégration de Windows SharePoint Services**, type `Partner Name` dans les **colonne 01** champ.  
  
11. Type `%XPATH=//pons:PurchaseOrder/pons:BillTo%` dans les **valeur colonne 01** , cliquez sur **OK**, puis cliquez sur **OK** pour quitter le **propriétés de Port d’envoi** boîte de dialogue.  
  
#### <a name="restart-the-send-port"></a>Pour redémarrer le port d'envoi  
  
1.  Dans le **Console Administration de BizTalk**, cliquez sur le **Ports d’envoi** nœud.  
  
2.  Avec le bouton droit `SendToDestination`, puis cliquez sur **désinscrire**.  
  
3.  Avec le bouton droit `SendToDestination`, puis cliquez sur **Démarrer**.  
  
4.  Fermer le **Console Administration de BizTalk**.  
  
## <a name="send-a-message-through-the-system"></a>Envoi d'un message via le système  
 Dans cette procédure, vous allez créer un formulaire InfoPath et le télécharger sur le site Web Windows SharePoint Services. L'adaptateur Windows SharePoint Services prend ce message, l'archive dans la bibliothèque de documents d'archive, puis l'envoie dans la bibliothèque de documents de destination. Cette procédure montre comment un document circule depuis un site Web SharePoint, via [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vers un site Web SharePoint Services, à l'aide de l'adaptateur Windows SharePoint Services.  
  
#### <a name="create-an-infopath-form-to-send-through-the-system"></a>Création d'un formulaire InfoPath pour envoi via le système  
  
1.  Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  Sur le côté gauche, sous **Documents**, cliquez sur `InfoPathSolutions`.  
  
3.  Cliquez sur le `PurchaseOrder` fichier pour afficher la **télécharger le fichier** boîte de dialogue, puis cliquez sur **ouvrir**. InfoPath va charger le formulaire.  
  
4.  Dans le **Purchase Order ID** , tapez `1002`.  
  
5.  Dans le **facturation** , tapez `John Doe`.  
  
6.  Dans le **quantité** , tapez `750`.  
  
7.  Dans le **Purchase Order Date** , tapez `1/2/2005`.  
  
8.  Cliquez sur **Enregistrer**.  
  
9. Dans le **enregistrer en tant que** boîte de dialogue, tapez `http://<server_name>/sites/WSSAdapterWalkthrough/Source`dans les **nom de fichier** champ, puis appuyez sur ENTRÉE.  
  
10. Type `PurchaseOrder2.xml` dans les **nom de fichier** champ, puis cliquez sur **enregistrer**.  
  
11. Fermez Microsoft Office InfoPath.  
  
12. Dans le navigateur Web, dans la barre de navigation supérieure, cliquez sur **Documents et listes**.  
  
13. Sous **bibliothèques de documents**, cliquez sur **Destination**.  
  
14. Votre message est désormais répertorié dans la bibliothèque de documents de destination. Vous y trouverez également une copie archivée dans la bibliothèque de documents d’Archive.  
  
15. Dans la bibliothèque de documents de destination, cliquez sur `PurchaseOrder1.xml`. Notez que ce fichier XML s'ouvre dans Microsoft Internet Explorer.  
  
16. Dans la bibliothèque de documents de destination, cliquez sur `PurchaseOrder2.xml`. Notez que le fichier XML est ouvert dans Microsoft Office InfoPath.  
  
> [!NOTE]
>  Dans la bibliothèque de documents de destination, les colonnes Nom de fichier et Nom du partenaire devraient contenir respectivement la valeur des champs Réf bon de commande et Facturer à.  
  
## <a name="summary"></a>Résumé  
 Cette procédure pas à pas vous a permis d'ajouter une intégration étroite à Microsoft InfoPath, à l'aide de l'adaptateur Windows SharePoint Services et du routage basé sur le contenu.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : Module 3 - l’accès à des propriétés SharePoint à partir d’une Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md) procédure pas à pas qui permet de compléter le travail que vous avez terminé cette procédure pas à pas, intègre un orchestration dans le projet et vous montre comment accéder aux propriétés de SharePoint à partir d’elle.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Procédures pas à pas de carte de Windows SharePoint Services](../core/windows-sharepoint-services-adapter-walkthroughs.md)