---
title: PartyResolution (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, parties
- orchestrations, examples
- parties, examples
- parties, orchestrations
- examples, routing
- orchestrations, parties
- examples, orchestrations
- examples, messages
- routing, messages
- messages, routing
ms.assetid: 220e6bc5-6f04-4f37-b0d0-f11c2cc14422
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be8d7e33cefd2272490bd2f01243ff03b0e7009a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="partyresolution-biztalk-server-sample"></a>PartyResolution (exemple BizTalk Server)
L'exemple PartyResolution illustre l'utilisation des orchestrations BizTalk avec la résolution de tiers pour acheminer les messages vers l'un des deux destinataires possibles.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple exécute plusieurs orchestrations qui illustrent les rôles suivants :  
  
-   orchestration de l'acheteur, qui permet de lancer le traitement des messages relatifs aux bons de commande ;  
  
-   orchestration du fournisseur, qui illustre la résolution de tiers entrants et sortants ;  
  
-   orchestrations ShipmentAgency1 et ShipmentAgency2, qui répondent à l'orchestration du fournisseur sur la base de l'adresse de livraison figurant sur le bon de commande.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 La résolution de tiers fait référence au processus qui consiste à déterminer l'expéditeur (tiers) d'un message. Par exemple, vous pouvez autoriser uniquement les tiers connus à envoyer un message. La résolution de tiers sortants est le processus qui consiste à déterminer les tiers destinataires d'un message.  
  
 Outre la résolution de tiers, cet exemple présente l'implémentation et l'utilisation des rôles. Par exemple, pour traiter la livraison d'un produit, vous créez un port d'envoi auquel vous envoyez un document demandant à un expéditeur de livrer le produit. Si vous avez le choix entre plusieurs expéditeurs, vous pouvez créer un rôle Expéditeur dans votre orchestration, plutôt que de créer plusieurs ports d'envoi dont la seule différence réside dans l'URL de l'expéditeur. Vous pouvez ensuite envoyer des messages relatifs à la livraison du produit au rôle Expéditeur. Vous créez des tiers, puis associez un port d'envoi à chaque tiers et certificat de tiers. Pour terminer, vous inscrivez chaque tiers au rôle Expéditeur pour l'activer. Dans l'orchestration, vous pouvez ensuite spécifier dynamiquement l'expéditeur auquel vous envoyez le message.  
  
 Cet exemple illustre également l'utilisation de la corrélation afin de faire correspondre le message entrant à l'instance d'orchestration adéquate.  
  
-   Les flux de processus d'entreprise pour l'acheteur, le fournisseur et les expéditeurs sont les suivants :  
  
-   Flux de processus d'entreprise de l'acheteur :  
  
    1.  Recevez le message de bon de commande envoyé par le service interne au format .xml.  
  
    2.  Envoyez le message de bon de commande au fournisseur.  
  
-   Flux de processus d'entreprise du fournisseur :  
  
    1.  Résolvez le tiers (résolution de tiers entrant) pour mettre à jour le tiers source sur la base d'un certificat de signature.  
  
    2.  Recevez un message d'activation (bon de commande) de l'acheteur.  
  
    3.  Envoyez un accusé de réception de bon de commande à l'acheteur.  
  
    4.  Vérifiez le pays ou la région de la livraison.  
  
    5.  Résolvez le tiers sortant pour rechercher l'agence d'expédition à utiliser. Aux États-Unis, l'agence d'expédition est ShipmentAgency2. Au Canada, l'agence d'expédition est ShipmentAgency1.  
  
    6.  Envoyez un message de demande d'ordre de livraison à l'agence d'expédition appropriée.  
  
    7.  Recevez l'accusé de réception d'ordre de livraison provenant de l'agence d'expédition appropriée.  
  
    8.  Envoyez un message d'avis d'expédition à l'agence d'expédition appropriée.  
  
    9. Recevez un accusé de réception d'avis d'expédition provenant de l'agence d'expédition appropriée.  
  
    10. Envoyez un message d'accusé de réception du bon de commande à l'acheteur.  
  
-   Flux de processus d'entreprise de l'agence d'expédition (identique pour les deux agences d'expédition) :  
  
    1.  Recevez un message de demande d'ordre de livraison provenant du fournisseur.  
  
    2.  Générez et envoyez un message d'accusé de réception du message de demande d'ordre de livraison.  
  
    3.  Recevez un message d'avis d'expédition du fournisseur.  
  
    4.  Générez et envoyez un message d'accusé de réception du message d'avis d'expédition.  
  
 Les énoncés suivants décrivent la conception de cet exemple :  
  
-   L'orchestration BuyerProcess.odx reçoit un message et utilise le pipeline personnalisé MimePartyResSendPipeline pour l'encoder et l'envoyer au fournisseur. Cette opération est effectuée à l'aide du Concepteur de pipeline pour générer et déployer un pipeline d'envoi personnalisé. Avant d'envoyer le message au fournisseur, celui-ci est signé numériquement à l'aide de la clé privée de l'acheteur, spécifiée dans les propriétés de groupe BizTalk dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   L'orchestration SupplierProcess.odx utilise le pipeline personnalisé MimePartyResReceivePipeline, qui inclut le Composant Décodeur MIME/SMIME, pour décoder le message et procéder à une résolution de tiers entrant à l'aide de la clé publique de l'acheteur pour résoudre et valider l'identité de celui-ci. Cette opération est effectuée en générant et en déployant un pipeline de réception personnalisé.  
  
-   L'orchestration du fournisseur lance ensuite POCorrelationSets, qui se base sur la propriété promue PONo. Celle-ci permettra de faire correspondre les messages entrants et sortants avec cette instance d'orchestration ultérieurement, car plusieurs actions d'envoi et de réception transitent par l'orchestration entière.  
  
-   L'orchestration du fournisseur implémente les liens de rôle pour traiter la résolution des tiers entrants et sortants. Elle utilise deux types de liens de rôle :  
  
    -   Type de lien de rôle Buyer_Supplier  
  
    -   Type de lien de rôle Supplier_Shipment  
  
-   Dans le Buyer_Supplier **lien de rôle** forme, le fournisseur est dans le rôle de fournisseur et l’acheteur au rôle consommateur car le fournisseur reçoit le premier message de l’acheteur. Lorsque l'orchestration du fournisseur envoie l'accusé de réception au rôle de l'acheteur, un port d'envoi est associé à l'acheteur et le message est envoyé à celui-ci via le port d'envoi spécifié. Pour trouver le port d’envoi, cliquez sur **BuyerAgency** dans les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, puis cliquez sur **propriétés**. Le port d’envoi s’affiche sous **Ports d’envoi**.  
  
-   L'orchestration utilise ensuite l'expression suivante pour renvoyer les informations du partenaire, puis génère un fichier XML dans un dossier via un appel à un assembly externe nommé CheckPartyName.  
  
    ```  
    Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty)  
    ```  
  
-   Dans le Supplier_Shipment **lien de rôle** forme, le rôle livraison inclut un port d’envoi contenant deux opérations qui sont utilisés pour envoyer le message du fournisseur à l’agence d’expédition appropriée en fonction du tiers de destination. Le rôle Fournisseur inclut un port de réception contenant deux opérations permettant de recevoir la réponse de l'agence d'expédition. La corrélation, basée sur la propriété PONo, est utilisée lors de l'envoi et de la réception de ces messages.  
  
    > [!NOTE]
    >  Lorsque vous lierez l'orchestration du fournisseur, vous remarquerez que seul un port d'envoi et deux ports de réception doivent être liés. Ceci s'explique par le fait que les ports d'envoi vers les tiers de destination sont déjà liés aux tiers. En outre, un des ports de réception dans l’orchestration contient deux opérations de réception, c’est le cas même si vous voyez trois **réception** formes, seulement deux d'entre elles doivent être liés.  
  
-   L'orchestration du fournisseur utilise la première ligne du code suivant pour obtenir l'agence d'expédition en appelant un assembly externe nommé QueryShipmentCatalogComponent. Elle utilise ensuite la deuxième ligne pour définir le tiers de destination pour le rôle Livraison.  
  
    ```  
    strShipmentName= objQueryShipmentCatalog.GetShipmentDetails(POMessage.MessagePart_1.POHeader.Address.Country);  
    Supplier_Shipment(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party(strShipmentName,"OrganizationName");  
    ```  
  
-   Shipper1Process.odx et Shipper2Process.odx sont générés pour recevoir le bordereau de livraison et l'avis d'expédition de SupplierProcess.odx, ainsi que pour renvoyer la réponse à SupplierProcess.odx. Dans les deux orchestrations d'expéditeur, la corrélation est utilisée et son type est basé sur la propriété promue PONo.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\Orchestrations\PartyResolution\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|BuyerBinding.xml, ShippingAgency1Binding.xml, ShippingAgency2Binding.xml, SupplierBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache. Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|PartyResolution.sln|Fichier de solution qui inclut tous les projets des sous-dossiers.|  
|PurchaseOrder.xml|Exemple d'entrée de bon de commande.|  
|Setup.bat|Il permet de créer et d'initialiser des parties de cet exemple.|  
|Dans le dossier \Buyer :<br /><br /> Buyer.btproj, BuyerProcess.odx|Projet et orchestration BizTalk qui permettent d'implémenter l'acheteur dans cet exemple.|  
|Dans le dossier \Catalog :<br /><br /> Catalog.xml|Permet de déterminer l'agence d'expédition selon la destination de livraison spécifiée dans le bon de commande.|  
|Dans le dossier \CheckPartyName :<br /><br /> AssemblyInfo.cs, CheckPartyName.csproj, Class1.cs|Projet et fichiers sources Microsoft Visual C# pour l'application CheckPartyName permettant d'accéder aux propriétés du tiers source.|  
|Dans le dossier \FilePolling :<br /><br /> App.ico, AssemblyInfo.cs, FilePolling.cs, FilePolling.csproj, FilePolling.resx, FilePolling.sln,|Solution, projet et source Visual c#, ainsi que les fichiers associés pour l'application FilePolling.<br /><br /> Cette application permet de rester informé sur l'état de progression de ce scénario automatisé.|  
|Dans le dossier \Pipeline\projectschema :<br /><br /> MimePartyResReceivePipeline.btp, MimePartyResSendPipeline.btp|Fichiers de pipeline de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisés par les différents rôles de cet exemple.|  
|Dans le dossier \QueryShipmentCatalogComponent :<br /><br /> AssemblyInfo.cs, QueryShipmentCatalog.cs, QueryShipmentCatalogComponent.csproj|Projet et fichiers sources Visual C# pour le composant QueryShipmentCatalog permettant d'accéder au catalogue de livraison défini dans le fichier Catalog.xml.<br /><br /> Le composant QueryShipmentCatalog détermine l'agence d'expédition utilisée par le fournisseur. Il utilise les données du fichier Catalog.xml pour déterminer l'expéditeur le plus approprié en fonction de sa situation géographique.|  
|Dans le dossier \Schemas :<br /><br /> PODeliveryReceipt.xsd, POPropertySchema.xsd, PurchaseOrder.xsd, PurchaseOrderAcknowledgement.xsd, Schemas.btproj, ShipmentAdvice.xsd, ShipmentAdviceAcknowledgement.xsd, ShipmentOrderAcknowledgement.xsd, ShipmentOrderRequest.xsd|Schémas utilisés par les divers rôles de cet exemple.|  
|Dans le dossier \ShipmentAgency1 :<br /><br /> ShipmentAdviceAck.btm, ShipmentAgency1.btproj, ShipmentOrderAck.btm, Shipper1Process.odx|Projet, orchestration et mappages BizTalk qui permettent d'implémenter ShipmentAgency1 dans cet exemple.|  
|Dans le dossier \ShipmentAgency2 :<br /><br /> ShipmentAdviceAck.btm, ShipmentAgency2.btproj, ShipmentOrderAck.btm, Shipper2Process.odx|Projet, orchestration et mappages BizTalk qui permettent d'implémenter ShipmentAgency2 dans cet exemple.|  
|Dans le dossier \Supplier :<br /><br /> PO_POAck.btm, PO_ShipmentOrderRequest.btm, ShipmentAdviceAck_PODeliveryReceipt.btm, ShipmentOrder_ShipmentAdvice.btm, Supplier.btproj, SupplierProcess.odx|Projet, orchestration et mappages BizTalk qui permettent d'implémenter le fournisseur dans cet exemple.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
> [!NOTE]
>  Avant de générer et d'initialiser l'exemple, vous devez veiller à ce que l'hôte BizTalk de type In-Process par défaut soit configuré comme étant approuvé par authentification. Pour plus d’informations, consultez [recommandations de sécurité de BizTalk Server Runtime](../core/biztalk-server-runtime-security-recommendations.md).  
  
 Le composant de pipeline MIME n'est pas pris en charge dans une instance d'hôte 64 bits. L'hôte associé au gestionnaire d'envoi et de réception pour l'adaptateur de FILE doit être configuré en tant qu'hôte 32 bits uniquement. Pour plus d’informations à ce sujet, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md). Si vous 32 bits seul un hôte est configuré sur le système et souhaitez l’utiliser, consultez [configuration de l’adaptateur de fichier](../core/configure-the-file-adapter.md) pour obtenir des instructions sur la configuration du ou des hôtes associés à l’adaptateur de fichier envoi et le Gestionnaire de réception.  
  
 Le certificat mentionné dans cette section doit être ajouté au magasin personnel du compte de connexion configuré pour l'instance d'hôte BizTalk de type In-Process par défaut qui signera les messages.  
  
 Par défaut, le fichier setup.bat indiqué ci-dessous installera l'exemple PartyResolution dans l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par défaut. Vous pouvez modifier ce fichier de manière à déployer l'exemple dans une nouvelle application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en l'ouvrant et en remplaçant la section précédée par l'instruction `@ECHO Deploy Assemblies...` par ce qui suit :  
  
```  
@ECHO Deploy Assemblies...  
  
btstask AddApp -ApplicationName:PartyResolutionSample -Description:"Party Resolution Orchestration sample from the SDK"  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Schemas\bin\Release\Schemas.dll -Options:GacOnAdd  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Pipeline\projectschema\bin\Release\ProjectSchema.dll -Options:GacOnAdd   
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Buyer\bin\Release\Buyer.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%BuyerBindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:ShipmentAgency1\bin\Release\ShipmentAgency1.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%ShipmentAgency1BindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:ShipmentAgency2\bin\Release\ShipmentAgency2.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%ShipmentAgency2BindingFileName%  
btstask AddResource -ApplicationName:PartyResolutionSample -Type:System.BizTalk:BizTalkAssembly  -Source:Supplier\bin\Release\Supplier.dll -Options:GacOnAdd  
btstask ImportBindings -ApplicationName:PartyResolutionSample -Source:%SupplierBindingFileName%  
```  
  
#### <a name="to-build-and-initialize-the-partyresolution-sample"></a>Pour créer et initialiser l'exemple PartyResolution  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Orchestrations\PartyResolution  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Compilation des projets de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple, puis déploiement des assemblys qui en résultent.  
  
    -   Crée et lie les ports d'envoi et de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
         Au cours de l'installation, vous pouvez recevoir les avertissements suivants ou des avertissements similaires. Vous pouvez les ignorer en toute sécurité.  
  
        ```  
        "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\PartyResolution.sln" (Buildtarget) (1) ->  
        "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj" (default target) (5) ->  
        "C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj" (default target) (5:2) ->  
        (CompileODX target) ->  
          C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\SupplierProcess.odx(831,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it [C:\ProgramFiles\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj]  
          C:\Program Files\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\SupplierProcess.odx(841,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it [C:\ProgramFiles\Microsoft BizTalk Server <version>\SDK\Samples\Orchestrations\PartyResolution\Supplier\Supplier.btproj]  
  
        ```  
  
3.  Démarrer **invite de commandes Visual Studio**.  
  
4.  Tapez les commandes suivantes pour installer les assemblys dans le Global Assembly Cache :  
  
    -   gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Schemas\bin\Release\schemas.dll  
  
    -   gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Pipeline\projectschema\bin\Release\ProjectSchema.dll  
  
    -   gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Buyer\bin\Release\Buyer.dll  
  
    -   gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\ShipmentAgency1\bin\Release\ShipmentAgency1.dll  
  
    -   gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\ShipmentAgency2\bin\Release\ShipmentAgency2.dll  
  
    -   gacutil -i [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Orchestrations\PartyResolution\Supplier\bin\Release\Supplier.dll  
  
5.  Obtenez un certificat de messagerie sécurisé auprès d'une autorité de certification (autorité tierce ou autorité de votre organisation). Une fois le certificat obtenu, exportez les clés publique et privée.  
  
6.  Pour importer la clé privée dans le magasin personnel du compte de connexion de l'instance d'hôte et la clé publique dans le magasin Autres personnes de l'ordinateur local, procédez comme suit :  
  
    1.  Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez le groupe BizTalk, puis **paramètres de plateforme**.  
  
    2.  Cliquez sur **Instances d’hôte** et recherchez le compte d’ouverture de session pour l’instance d’hôte In-Process par défaut. Dans une installation par défaut, l'hôte de type In-Process par défaut doit être nommé BizTalkServerApplication.  
  
    3.  Cliquez sur **Démarrer**, puis sur **Exécuter**. Dans le **exécuter** , tapez **mmc.exe**, puis cliquez sur **OK**. Entrez le mot de passe correct du compte de connexion de l'instance d'hôte pour ouvrir la console MMC (Microsoft Management Console) sous ce compte.  
  
    4.  Dans le menu **Fichier** , cliquez sur **Ajouter/Supprimer un composant logiciel enfichable**.  
  
    5.  Dans le **ajouter ou supprimer des composants logiciel enfichables** boîte de dialogue, sélectionnez **certificats**, puis cliquez sur **ajouter**.  
  
    6.  Dans le **enfichable Certificats** boîte de dialogue, sélectionnez **mon compte d’utilisateur**, puis cliquez sur **Terminer**.  
  
    7.  Dans le **ajouter ou supprimer des composants logiciel enfichables** boîte de dialogue, sélectionnez **certificats**, puis cliquez sur **ajouter**.  
  
    8.  Dans le **enfichable Certificats** boîte de dialogue, sélectionnez **compte d’ordinateur**, puis cliquez sur **suivant**.  
  
    9. Dans le **sélectionner un ordinateur** boîte de dialogue, sélectionnez **ordinateur Local**, puis cliquez sur **Terminer**.  
  
    10. Dans le **ajouter ou supprimer des composants logiciel enfichables** boîte de dialogue, cliquez sur **OK**.  
  
    11. Développez le **certificats - utilisateur actuel** nœud, puis **personnel**. Avec le bouton droit **certificats**, cliquez sur **toutes les tâches**, puis cliquez sur **importation**.  
  
    12. Importez la clé privée et indiquez un mot de passe dans l'Assistant.  
  
    13. Développez le **certificats (ordinateur Local)** nœud, puis **autres personnes**. Avec le bouton droit **certificats**, cliquez sur **toutes les tâches**, puis cliquez sur **importation**.  
  
    14. Importez la clé publique.  
  
7.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit le **groupe BizTalk** nœud, puis cliquez sur **propriétés**. Dans le **groupe BizTalk - propriétés du groupe** boîte de dialogue, sélectionnez **certificat**.  
  
8.  Dans le **certificat** boîte de dialogue, cliquez sur **Parcourir** et sélectionnez la clé privée que vous venez d’importer. Le certificat spécifié ici permet de signer le message sortant. Cliquez sur **OK**.  
  
9. Pour mettre à jour le tiers BuyerAgency dans cet exemple, procédez comme suit :  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, sélectionnez **Parties**.  
  
    2.  Avec le bouton droit **BuyerAgency** puis cliquez sur **propriétés**. Dans le **BuyerAgency - propriétés de tiers** boîte de dialogue, sélectionnez **général**.  
  
    3.  Sous le **alias** section de la boîte de dialogue Ajouter un nouvel alias avec le nom et un jeu de qualificatifs sur **WindowsUser**. Définissez la valeur sur un nom d’utilisateur au format de \<domaine\nom d’utilisateur > (par exemple, domaine\utilisateur).  
  
    4.  Sélectionnez **certificat** puis cliquez sur **Parcourir** et sélectionnez la clé publique que vous venez d’importer. Le certificat spécifié ici permet de valider l'identité de l'expéditeur du message entrant. Cliquez sur **OK**.  
  
10. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **paramètres de plateforme**, puis sélectionnez **hôtes**.  
  
11. Avec le bouton droit **BizTalkServerApplication** puis cliquez sur **propriétés**. Dans le **BizTalkServerApplication - propriétés de l’hôte** boîte de dialogue, sélectionnez **certificats**.  
  
12. Cliquez sur **Parcourir** et sélectionnez la clé privée que vous venez d’importer. Le certificat spécifié ici permet de déchiffrer les messages entrants. Cliquez sur **OK**.  
  
13. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **paramètres de plateforme**, puis sélectionnez **Instances d’hôte**.  
  
14. Avec le bouton droit **BizTalkServerApplication** puis cliquez sur **redémarrer**.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-partyresolution-sample"></a>Pour exécuter l'exemple PartyResolution  
  
1.  Exécutez FilePolling.exe à partir du dossier suivant :  
  
     *\<Exemples de chemin d’accès >*\Orchestrations\PartyResolution\FilePolling\bin\Debug  
  
2.  Cliquez sur **d’interrogation de démarrer**.  
  
3.  Collez une copie du fichier d'instance de bon de commande fourni, PurchaseOrder.xml, dans le dossier suivant :  
  
     *\<Exemples de chemin d’accès >*\Orchestrations\PartyResolution\FileDrop\PurchaseOrder  
  
4.  Observez la séquence de messages fournis sous forme de MessageBoxes qui vous informent de la progression de l'exemple :  
  
    1.  Lorsque le fournisseur reçoit le bon de commande de l'acheteur.  
  
    2.  Lorsqu'une demande d'ordre de livraison est reçue de l'agence d'expédition 1 ou 2.  
  
    3.  Lorsqu'un avis d'expédition est reçu par l'agence d'expédition 1 ou 2.  
  
    4.  Lorsque le fournisseur envoie l'accusé de réception du bon de commande à l'acheteur.  
  
5.  Cliquez sur **Exit** pour fermer le programme interrogation de fichiers.  
  
> [!NOTE]
>  Modifiez la balise Pays dans PurchaseOrder.xml sur « FR », puis répétez les étapes 2 et 3. Vous noterez que l'ordre de livraison est désormais envoyé à l'agence d'expédition 2.  
  
## <a name="uninstalling-this-sample"></a>Désinstallation de l'exemple  
  
#### <a name="to-uninstall-the-partyresolution-sample"></a>Pour désinstaller l'exemple PartyResolution  
  
1.  À un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) à \< *exemples de chemin*> \Orchestrations\ PartyResolution\\.  
  
2.  Exécutez Cleanup.bat.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline résolution du tiers](../core/party-resolution-pipeline-component.md)   
 [Comment configurer le composant de Pipeline encodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)   
 [Comment configurer le composant de Pipeline décodeur MIME-SMIME](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)   
 [Orchestrations (dossier d’exemples BizTalk Server)](../core/orchestrations-biztalk-server-samples-folder.md)