---
title: "Comment créer des liens de rôle dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc386ac2-a851-4342-9ceb-0b6faddf4ece
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e40a77392af9e97791cd9afbacc8f0b533f60288
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-role-links-in-orchestrations"></a>Création de liens de rôle dans des orchestrations
Voici les tâches de base que vous devez effectuer pour utiliser des liens de rôle dans votre orchestration :  
  
-   Créez des tiers et des ports d'envoi et associez-les les uns aux autres.  
  
-   Utilisez la procédure suivante pour créer des types de lien de rôle et ajouter des types de port.  
  
    |Pour créer un type de lien de rôle|  
    |--------------------------------|  
    |1.  Dans la fenêtre Vue Orchestration, développez **Types**, avec le bouton droit **les Types de liens de rôle**, puis cliquez sur **nouveau Type de lien de rôle**.<br />2.  Cliquez sur le type de lien de rôle que vous venez de créer. Dans la fenêtre Propriétés, dans le **identificateur** , tapez `Provider_Consumer_RoleLinkType`.<br />3.  Développez **Provider_Consumer_RoleLinkType**, puis cliquez sur **Role_1**. Dans la fenêtre Propriétés, dans le **identificateur** , tapez `ConsumerRole`.<br />4.  Avec le bouton droit **ConsumerRole**, puis cliquez sur **ajouter un Type de Port**. L'Assistant Type de port démarre.<br />5.  Sur le **l’Assistant Type de Port** , cliquez sur **suivant**.<br />6.  Sur le **sélectionner un Type de Port ou créer un nouveau Type de Port** , sélectionnez **créer un nouveau Type de Port**, puis **nom du Type de Port**, type `ConsumerPortType`.<br />7.  Pour **modèle de Communication**, sélectionnez **unidirectionnel**et pour **Restrictions d’accès**, sélectionnez **Public - aucune limite**. Cliquez sur **Suivant**.<br />8.  Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.<br />9. Avec le bouton droit **Provider_Consumer_RoleLinkType**, puis cliquez sur **nouveau rôle**.<br />10. Cliquez sur **Role_1**, puis, dans la fenêtre Propriétés, dans le **identificateur** , tapez `ProviderRole`.<br />11. Avec le bouton droit **ProviderRole**, puis cliquez sur **ajouter un Type de Port**. L'Assistant Type de port démarre.<br />12. Sur le **l’Assistant Type de Port** , cliquez sur **suivant**.<br />13. Sur le **sélectionner un Type de Port ou créer un nouveau Type de Port** , sélectionnez **créer un nouveau Type de Port**, puis **nom du Type de Port**, type `ProviderPortType`.<br />14. Pour **modèle de Communication**, sélectionnez **unidirectionnel**et pour **Restrictions d’accès**, sélectionnez **Public - aucune limite**. Cliquez sur **Suivant**.<br />15. Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**. **Remarque :** ports configurés placés à l’intérieur des liens de rôle ne conservent pas leurs informations de liaison associée.|  
  
     Dans la procédure précédente, vous créez un type de lien de rôle contenant deux rôles : un ProviderRole qui recevra et traitera les messages du consommateur et un ConsumerRole dont le port d'envoi sera utilisé par votre orchestration pour envoyer des messages au consommateur.  
  
> [!NOTE]
>  Le type de lien de rôle peut contenir un rôle de fournisseur et un rôle de consommateur, et il peut inclure un de chaque ou l'un des deux en fonction des besoins de votre processus d'entreprise.  
  
-   Pour ajouter des liens de rôle à votre orchestration, suivez la procédure ci-dessous.  
  
    |Pour créer un lien de rôle à l'aide de l'Assistant Lien de rôle|  
    |---------------------------------------------------------|  
    |1.  Dans l’orchestration de boîte à outils, faites glisser le **lien de rôle** forme sur l’aire de conception. L'Assistant Lien de rôle démarre.<br />2.  Sur le **Bienvenue dans l’Assistant lien de rôle** , cliquez sur **suivant**.<br />3.  Sur le **Nomlienrôle** page, dans le **nom** , tapez `Provider_Consumer`. Cliquez sur **Suivant**.<br />4.  Sur le **Type de lien de rôle** page, sélectionnez **utiliser un Type de lien de rôle existant**. Dans le **nom de Type de lien de rôle** la liste déroulante, sélectionnez **Provider_Consumer_RoleLinkType**. Cliquez sur **Suivant**.<br />5.  Sur le **Identification du rôle** page, sélectionnez **ProviderRole** à partir de la **quel rôle cette orchestration implémentera pour recevoir et traiter les messages des partenaires ?** liste déroulante. L’Assistant sélectionne automatiquement **ConsumerRole** pour **cette orchestration utilisera le rôle ci-dessous pour envoyer des messages aux partenaires sur des ports du rôle**. Cliquez sur **Suivant**.<br />6.  Sur le **utilisation du lien de rôle** page, sélectionnez **envoyer le premier message au rôle de mon partenaire**. Cliquez sur **Terminer**.|  
  
     Dans la procédure précédente, vous précisez la définition du ConsumerRole en tant que rôle initiateur. Cela signifie que votre orchestration enverra le premier message au consommateur via le port fourni par le ConsumerRole et que le ProviderRole recevra ensuite le message retourné par le consommateur pour traitement.  
  
    > [!NOTE]
    >  S’il existe un seul rôle dans le type de lien de rôle, vous devez définir votre rôle dans le processus d’entreprise en sélectionnant le **rôle du fournisseur : recevoir le premier message** ou **rôle consommateur : envoyer le premier message** au lieu d’effectuer l’étape 5 de la procédure précédente.  
  
-   Concevez votre processus d'entreprise. Vous pouvez tirer parti d'ensembles de corrélations pour vous assurer qu'un message entrant correspond à l'instance appropriée d'une orchestration.  
  
-   Associez les ports à **envoyer** et **réception** formes. En outre, suivez les instructions suivantes :  
  
    -   Si le rôle initiateur est un consommateur pour envoyer des messages, définissez explicitement la **DestinationParty** , propriété (une fois et une seule fois) dans votre orchestration. Pour ce faire, définissez la valeur de la **DestinationParty** dans les **Expression** forme, comme dans l’exemple suivant, où ConfirmOrder est le nom d’un lien de rôle et PartnerName et OrganizationName sont des paramètres d’un tiers :  
  
        ```  
        ConfirmOrder(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party("PartnerName", "OrganizationName");  
        ```  
  
    -   Si le rôle initiateur est un fournisseur pour la réception des messages, le **DestinationParty** propriété est automatiquement initialisée par le récepteur. Le **DestinationParty** est défini sur le fournisseur lui-même. Le **SourceParty** propriété est en lecture seule et est fournie via un composant de pipeline approuvé pour résoudre le nom du tiers en fonction de l’identificateur de sécurité (SID) de l’expéditeur ou sur un certificat associé au tiers. L’hôte qui exécute le composant de pipeline doit être marquée comme **approuvé par authentification**. Vous pouvez obtenir la valeur de la **SourceParty** dans les **Expression** forme à l’aide de l’exemple de code suivant :  
  
        ```  
        PartyName = Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty);  
        ```  
  
## <a name="examples-of-using-role-links"></a>Exemples d'utilisation de liens de rôle  
  
-   [PartyResolution (exemple BizTalk Server)](../core/partyresolution-biztalk-server-sample.md)  
  
-   Télécharger l’exemple du Kit de développement logiciel « Using Role Links » dans les exemples de code BizTalk Server disponibles à l’adresse [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens de rôle dans les Orchestrations](../core/using-role-links-in-orchestrations.md)   
 [L’utilisation de la forme de lien de rôle](../core/how-to-use-the-role-link-shape.md)   
 [Comment utiliser l’Assistant lien de rôle](../core/how-to-use-the-role-link-wizard.md)