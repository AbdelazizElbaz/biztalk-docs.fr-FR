---
title: "L’importation BPEL (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BPEL, orchestrations
- examples, orchestrations
- examples, BPEL Import Wizard
- BPEL, examples
- BPEL Import Wizard, examples
- BPEL Import Wizard, orchestrations
ms.assetid: 3fc70608-ccd9-4249-b238-c09fc6551db1
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13b0f446dab1d597e9dd2435e2bb5f40b3fd37ce
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="bpel-import-biztalk-server-sample"></a>Importation BPEL (exemple BizTalk Server)
L'exemple Importation BPEL montre comment créer une orchestration à partir d'une description de processus Business Process Execution Language (BPEL) et des artefacts qui y sont associés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Wide World Importers est une société de transport qui offre aux détaillants des services d'expédition automatisés. Plus précisément, Wide World Importers permet aux détaillants d'effectuer les opérations suivantes :  
  
-   commander des expéditions de commande ;  
  
-   suivre les expéditions ;  
  
-   vérifier les expéditions ;  
  
-   vérifier la facturation et le paiement des expéditions.  
  
 Si la disponibilité de ces services peut être représentée à l'aide d'un document WSDL (Web Services Description Language), un document BPEL décrit la manière classique dont des fabricant de produits sont supposés faire appel aux services et comment ils peuvent attendre des réponses de Wide World Importers.  
  
 Lorsque Northwind Traders fait appel à Wide World Importers pour gérer ses expéditions, il reçoit un fichier BPEL et des artefacts associés décrivant l'ensemble de l'interaction. À l'aide du fichier BPEL, Northwind Traders crée une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (BPELShipping) permettant de traiter automatiquement les commandes adressées à Wide World Importers.  
  
 Cet exemple vous guide tout au long de ce scénario dans lequel l'application BPELShipping :  
  
1.  reçoit une commande du système de commande client de Northwind Traders :  
  
2.  envoie une demande d'expédition à Wide World Importers et demande confirmation ;  
  
3.  reçoit une confirmation de demande d'expédition de Wide World Importers ;  
  
4.  reçoit une notification d'enlèvement de Wide World Importers ;  
  
5.  reçoit des messages relatifs à l'état de l'expédition jusqu'au moment où le client reçoit la livraison ;  
  
6.  reçoit une facture de Wide World Importers ;  
  
7.  répond à Wide World Importers par un accusé de réception de la facture ;  
  
8.  reçoit une confirmation de paiement de Wide World Importers ;  
  
9. envoie une confirmation de livraison finale au système de commande.  
  
 Une application BizTalk distincte (ShipperProcess) permet de simuler l'activité de Wide World Importers en relation avec cet exemple. L'application BPELShipping communique avec ShipperProcess à l'aide du transport FILE qui utilise des emplacements de système de fichiers communs pour la communication.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 BPEL pour services Web est un langage basé sur XML destiné à décrire le processus d'entreprise de façon à ce qu'il soit aisément partageable entre des sociétés différentes désireuses de commercer entre elles à l'aide de services Web. BPEL décrit comment gérer le processus d'entreprise au niveau du protocole d'entreprise, mais ne décrit pas le processus interne d'une société, par exemple, les étapes de traitement d'un bon de commande reçu d'un partenaire. Cette exemple est conçu pour montrer comment importer des fichiers BPEL et les fichiers WSDL correspondants, les convertir en une orchestration, puis commencer à exécuter le processus d'entreprise avec le partenaire.  
  
 La section ci-après décrit pas à pas les procédures d'importation des fichiers BPEL et WSDL et de conversion de ces derniers en une orchestration permettant d'interagir avec une application BizTalk prégénérée (ShipperProcess). Si vous suivez ces étapes, vous ne devez pas exécuter la procédure intitulée « Pour créer et initialiser l'application BPELShipping ».  
  
#### <a name="to-import-from-bpel-and-build-a-working-solution"></a>Pour importer à partir de BPEL et créer une solution de travail  
  
1.  Dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, cliquez sur **nouveau**, puis cliquez sur **projet**.  
  
    > [!NOTE]
    >  Avant d'exécuter cette procédure, vous devez configurer l'application ShipperProcess pour créer les processus et projets de schéma correspondants.  
  
2.  Dans le **nouveau projet** boîte de dialogue, dans le volet Types de projets, sélectionnez **BizTalk (projets)**. Dans le volet Modèles, sélectionnez **projet d’importation BPEL BizTalk Server**.  
  
3.  Dans le **nom** , entrez **BPELShipping**.  
  
    > [!NOTE]
    >  Si vous utilisez un autre nom, vous pouvez rencontrer des problèmes avec l'étape de liaison finale.  
  
4.  Sélectionnez un emplacement pour le projet, puis cliquez sur **OK** pour démarrer l’Assistant Importation BPEL.  
  
5.  Sur le **Bienvenue** , cliquez sur **suivant**.  
  
6.  Sur le **sélectionnez fichiers BPEL, WSDL et XSD** , cliquez sur **Parcourir**.  
  
7.  Sélectionnez tous les fichiers à partir de la \< *exemples de chemin*\>\Orchestrations\BPELImport\BPELSource, dossier, cliquez sur **ouvrir**, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Au cours de cette étape, vous sélectionnez les fichiers BPEL et WSDL pour décrire le processus d'entreprise et les fichiers XSD pour représenter les schémas de document commercial.  
  
8.  Sur le **sélectionner les fichiers WSDL pour les servicesWeb** , cliquez sur **Terminer**.  
  
9. Après que l'Assistant Importation BPEL a signalé une importation réussie, fermez l'Assistant. Le projet est maintenant créé.  
  
10. À la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) à l’emplacement du projet.  
  
11. Exécutez la commande suivante :  
  
     **sn – k BPELShipping.snk**  
  
12. Dans l’Explorateur de solutions, cliquez sur le **BPELShipping** de projet, puis cliquez sur **propriétés**.  
  
13. Sous **Common Properties\Assembly**, sélectionnez le fichier de clé d’assembly **BPELShipping.snk** créé à l’étape 11, puis cliquez sur **OK**.  
  
14. Dans l'Explorateur de solutions, sélectionnez tous les fichiers .xsd, puis supprimez-les.  
  
15. Dans l’Explorateur de solutions, sélectionnez **ajouter une référence**, puis, dans le **projets** , cliquez sur **Parcourir**.  
  
16. Sélectionnez **ShippingSchemas.dll** à partir de l’emplacement \< *exemples de chemin*\>\Orchestrations\BPELImport\Solution\ShipperProcess\ShippingSchemas\bin\Development, et puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  La section « Pour créer et initialiser l'application ShipperProcess » contient des instructions sur la manière de procéder.  
  
17. Dans l’Explorateur de solutions, double-cliquez sur **OrderShippingProcess.bpel.odx**.  
  
18. Sur le **vue** menu, sélectionnez **autres fenêtres/Vue Orchestration**.  
  
19. Dans la fenêtre Vue Orchestration, cliquez sur **propriétés d’Orchestration** puis cliquez sur **fenêtre Propriétés**.  
  
20. Dans la fenêtre Propriétés, définissez la **Orchestration Exportable** propriété **False**.  
  
21. Dans l’Explorateur de solutions, double-cliquez sur **OrderShipping.wsdl.odx**.  
  
22. Dans la fenêtre Vue Orchestration, développez **les Types de messages de Types de/à parties multiples**.  
  
23. Développez **InvoiceAckMessageType** puis cliquez sur **InvoiceAckMessagePart**.  
  
24. Dans la fenêtre Propriétés, développez le **Type** champ, puis sélectionnez **schémas/sélectionner dans l’Assembly référencé**.  
  
25. Dans le **sélectionner le Type d’artefact** boîte de dialogue, cliquez sur **ShippingSchemas**, sélectionnez le **Imported_InvoiceAckMessage** , puis tapez **OK**.  
  
    > [!NOTE]
    >  Dans les étapes 23 à 25, vous remplacez le type de message des services participant au processus BPEL par le type de message correspondant décrit dans ShippingSchemas.  
  
26. Répétez les étapes 23 à 25 pour chaque type de message à l'aide des valeurs suivantes.  
  
    |Partie du message|type de message|  
    |------------------|------------------|  
    |InvoiceMessagePart|ShippingSchemas.Imported_InvoiceMessage|  
    |OrderAckMessagePart|ShippingSchemas.Imported_OrderAckMessage|  
    |OrderMessagePart|ShippingSchemas.Imported_OrderMessage|  
    |PaymentConfirmationMessagePart|ShippingSchemas.Imported_PaymentConfirmationMessage|  
    |PickupNotificationMessagePart|ShippingSchemas.Imported_PickupNotificationMessage|  
    |ShipConfirmationMessagePart|ShippingSchemas.Imported_ShipConfirmationMessage|  
    |ShippingHistoryPart|ShippingSchemas.Imported_ShippingHistory|  
    |ShipRequestAckMessagePart|ShippingSchemas.Imported_ShipRequestAckMessage|  
    |ShipRequestMessagePart|ShippingSchemas.Imported_ShipRequestMessage|  
    |ShipStatusMessagePart|ShippingSchemas.Imported_ShipStatusMessage|  
  
27. Dans l’Explorateur de solutions, cliquez sur le **BPELShipping** de projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
28. Sélectionnez tous les fichiers .btm à l’emplacement \< *exemples de chemin*\>\Orchestrations\BPELImport\Solution\BPELShipping\BPELShipping.  
  
29. Dans la fenêtre Vue Orchestration, localisez le **assignation du Message** forme nommée MessageAssignment_1 in ConstructMessage1 et supprimez-le.  
  
30. Dans la boîte à outils, faites glisser un **transformer** mettre en forme dans la forme ConstructMessage1.  
  
31. Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) et ouvrez le **transformer la Configuration** boîte de dialogue.  
  
32. Sélectionnez **mappage existant**.  
  
33. Sélectionnez le nom de mappage complet **BPELShipping.Order2ShipRequest**.  
  
34. Sélectionnez la source en tant que **ordre. OrderMessagePart**.  
  
35. Sélectionnez la destination **ship_request. ShipRequestMessagePart** et cliquez sur **OK**.  
  
36. Répétez les étapes 29 à 35 pour chacune de la **assignation du Message** des formes et les remplacer par **transformer** formes d’après le tableau suivant.  
  
    |Forme à remplacer|Mappage à utiliser|Document source|Document de destination|  
    |----------------------|----------------|---------------------|--------------------------|  
    |MessageAssignment_2|BPELShipping.Order2OrderAck|order.OrderMessagePart|order_ack.OrderAckMessagePart|  
    |MessageAssignment_3|BPELShipping.Order2OrderNAck|order.OrderMessagePart|order_ack.OrderAckMessagePart|  
    |MessageAssignment_4|BPELShipping.Order2ShipHistory|order.OrderMessagePart|ship_history.ShippingHistoryPart|  
    |MessageAssignment_5|BPELShipping.ShipHistory2Completed|order.OrderMessagePart|ship_history.ShippingHistoryPart|  
    |MessageAssignment_6|BPELShipping.Invoice2Ack|Invoice.InvoiceMessagePart|invoice_ack.InvoiceAckMessagePart|  
    |MessageAssignment_7|BPELShipping.Order2FinalConfirmation|order.OrderMessagePart|order_shipped.OrderAckMessagePart|  
  
37. Enregistrez l'orchestration.  
  
38. Double-cliquez sur **Rule_1** dans les **décider** forme **Decision_1**.  
  
39. Dans l'Éditeur d'expression BizTalk, remplacez  
  
     ship_request_ack(BPELShipping.Ship_Acknowledged) == true  
  
     par  
  
     ship_request_ack(ShippingSchemas.Ship_Acknowledged) == true  
  
40. Double-cliquez sur le **boucle** forme nommée **Loop_1**.  
  
41. Dans l'Éditeur d'expression BizTalk, remplacez  
  
     ship_history(BPELShipping.Ship_Completed) == true  
  
     par  
  
     ship_history(ShippingSchemas.Ship_Completed) == true  
  
42. Double-cliquez sur **Rule_2** dans les **décider** forme **Decision_2**.  
  
43. Dans l'Éditeur d'expression BizTalk, remplacez  
  
     ship_status(BPELShipping.ShipStatus) == "DONE"  
  
     par  
  
     ship_status(ShippingSchemas.ShipStatus) == "DONE"  
  
44. Dans la vue Orchestration, développez **Types/Types de corrélation** et cliquez sur **_OrderCorrelationSet_Type\_**.  
  
45. Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) sur **propriétés de corrélation**.  
  
46. Dans les propriétés à mettre en corrélation dans le volet, cliquez sur **BPELShipping.OrderID**, puis cliquez sur **supprimer**.  
  
47. Dans le volet Propriétés disponibles, développez **schémas d’expédition**, sélectionnez **ID de commande**, puis cliquez sur **ajouter**.  
  
48. Cliquez sur **OK**.  
  
49. Enregistrez tous les fichiers, puis générez la solution.  
  
50. déployer la solution ;  
  
51. Accédez à l’emplacement \< *exemples de chemin*\>\Orchestrations\BPELImport\Solution\BPELShipping, puis double-cliquez sur **BindAndStartOnly.bat** pour lier et démarrer le orchestration.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\Orchestrations\BPELImport  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|BPELSource\InvoiceAckMessage.xsd|Schéma d'accusé de réception de facture.|  
|BPELSource\InvoiceMessage.xsd|Schéma de facture.|  
|BPELSource\OrderAckMessage.xsd|Schéma d'accusé de réception de commande.|  
|BPELSource\OrderHeader.xsd|Schéma d'en-tête de commande.|  
|BPELSource\OrderMessage.xsd|Schéma de message de commande.|  
|BPELSource\OrderShipping.wsdl|Fichier WSDL désigné par BPEL.|  
|BPELSource\OrderShippingProcess.bpel|Flux de processus BPEL.|  
|BPELSource\PaymentConfirmationMessage.xsd|Message de confirmation de paiement.|  
|BPELSource\PickupNotificationMessage.xsd|Message de notification d'enlèvement.|  
|BPELSource\ShipConfirmationMessage.xsd|Message de confirmation d'expédition.|  
|BPELSource\ShippingHistory.xsd|Document de l'historique d'expédition.|  
|BPELSource\ShipRequestAckMessage.xsd|Accusé de livraison de demande d'expédition.|  
|BPELSource\ShipRequestMessage.xsd|Demande de demande d'expédition.|  
|BPELSource\ShipStatusMessage.xsd|Message d'état d'expédition.|  
|Solution\bindings\BPELBindings.xml|Fichier de liaison spécifiant des liaisons de port pour l'orchestration BPELShipping.|  
|Solution\bindings\ShipperBindings.xml|Fichier de liaison spécifiant des liaisons de port pour l'orchestration ShipperProcess.|  
|Solution\BPELShipping\BindAndStartOnly.bat|Fichier de commandes pour la liaison et le démarrage de l'orchestration BPELImport après sa création manuelle et son déploiement.|  
|Solution\BPELShipping\cleanup.bat|Fichier de commandes à utiliser pour supprimer le processus BPELShipping.|  
|Solution\BPELShipping\Setup.bat|Fichier de commandes à utiliser pour installer et démarrer l'exemple BPELShipping fourni.|  
|Solution\BPELShipping\BPELShipping.sln|Exemple BPELShipping prégénéré.|  
olution\BPELShipping\BPELShipping\Invoice2Ack.btm|Facture pour mappage d'accusé de réception de facture.|  
|Solution\BPELShipping\BPELShipping\Order2FinalConfirmation.btm|Mappage à convertir à partir du message de commande vers la confirmation de livraison finale.|  
|Solution\BPELShipping\BPELShipping\Order2OrderAck.btm|Mappage à convertir à partir du message de commande vers l'accusé de réception de commande.|  
|Solution\BPELShipping\BPELShipping\Order2OrderNack.btm|Mappage à convertir à partir du message de commande vers l'accusé de réception négatif de commande.|  
|Solution\BPELShipping\BPELShipping\Order2ShipHistory.btm|Mappage à convertir à partir du message de commande vers le document de l'historique d'expédition.|  
|Solution\BPELShipping\BPELShipping\Order2ShipRequest.btm|Mappage à convertir à partir du message de commande vers la demande d'expédition de commande.|  
|Solution\BPELShipping\BPELShipping\ShipRequest2Completed.btm|Mappage pour définir l'historique de l'expédition comme terminé.|  
|Solution\ShipperProcess\setup.bat|Fichier de commandes pour générer, déployer, lier et démarrer l'orchestration de l'application auxiliaire ShipperProcess et ses ports.|  
|Solution\ShipperProcess\cleanup.bat|Fichier de commandes pour arrêter, annuler l'inscription et annuler le déploiement de l'orchestration de l'application auxiliaire ShipperProcess et de ses ports.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 La première étape consiste à créer et initialiser l'application ShipperProcess utilisée pour simuler Wide World Importers.  
  
#### <a name="to-build-and-initialize-the-shipperprocess-application"></a>Pour créer et initialiser l'application ShipperProcess  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  À partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) dans le dossier suivant :  
  
     *\<Exemples de chemin d’accès\>*\Orchestrations\BPELImport\Solution\ShipperProcess  
  
3.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   crée le projet ShippingSchemas contenant les schémas utilisés dans les processus ShipperProcess et BPELShipping ;  
  
    -   crée le processus ShipperProcess ;  
  
    -   déploie les projets ShippingSchemas et ShipperProcess ;  
  
    -   crée et lie les ports d'envoi et de réception utilisés par ShipperProcess ;  
  
    -   démarre les ports utilisés par ShipperProcess ;  
  
    -   inscrit et démarre l'orchestration ShipperProcess.  
  
 Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation. Un ou plusieurs des avertissements suivants peuvent s'afficher. Vous pouvez les ignorer.  
  
```  
The 'http://contoso.org/samples/Fragments:XXXX' element is not declared. An error occurred at , (35, 16).  
<SAMPLE_LOCATION>\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): warning X4014: convoy processing will not occur -- check your protocol if you were expecting it  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(667,22): convoy found at 'activate receive(Receive_ShipOrder.Operation_1, Request, initialize Correl)'  
<SAMPLE_LOCATION>\Samples\Orchestrations\BPELImport\Solution\ShipperProcess\ShipperProcess\ShipperProcess.odx(701,13): and 'receive(ReceiveInvoiceAck.Operation_1, Invoice_Ack, Correl)'  
```  
  
> [!NOTE]
>  Si vous avez exécuté la procédure décrite dans la section « Pour importer à partir de BPEL et créer une solution de travail », vous ne devez pas exécuter la procédure suivante.  
  
#### <a name="to-build-and-initialize-the-bpelshipping-application"></a>Pour créer et initialiser l'application BPELShipping  
  
1.  > [!WARNING]
    >  Avant d'exécuter cette procédure, vous devez exécuter la procédure ci-dessus intitulée « Pour créer et initialiser l'application ShipperProcess ».  
  
     À partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) dans le dossier suivant :  
  
     *\<Exemples de chemin d’accès\>*\Orchestrations\BPELImport\Solution\BPELShipping  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   crée le projet BPELShipping ;  
  
    -   déploie le projet BPELShipping ;  
  
    -   crée et lie les ports d'envoi et de réception utilisés par le processus BPELShipping ;  
  
    -   démarre les ports utilisés par le processus BPELShipping ;  
  
    -   inscrit et démarre l'orchestration BPELShipping.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-bpel-import-sample"></a>Pour exécuter l'exemple Importation BPEL  
  
1.  Copie le **fichier** de fichiers à partir de la  *\<exemples de chemin\>*dossier \Orchestrations\BPELImport\Solution à la \< *exemples de chemin\>* \Orchestrations\BPELImport\Solution\Ports\ReceiveOrder dossier.  
  
2.  L’orchestration récupère ce fichier comme une commande à partir du système de traitement de commande client, de BPELShipping s’exécute via le processus d’expédition, et génère un fichier dans le \< *exemples de chemin*\>\ Dossier de Orchestrations\BPELImport\Solution\Ports\SendOrder et \< *exemples de chemin*\>\Orchestrations\BPELImport\Solution\Ports\FinalConfirmation dossier. Le format du nom de ces fichiers est \< *MessageID*\>.xml, où  *\<MessageID\>*  est le GUID généré pour identifier de façon unique le Message.  
  
## <a name="uninstalling-this-sample"></a>Désinstallation de l'exemple  
  
#### <a name="to-uninstall-the-bpel-import-sample"></a>Pour désinstaller l'exemple Importation BPEL  
  
1.  À un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) à \< *exemples de chemin*\>\Orchestrations\BPELImport\BPELShipping.  
  
2.  Exécutez Cleanup.bat.  
  
3.  Accédez à \< *exemples de chemin d’accès*\>\Orchestrations\BPELImport\ShipperProcess.  
  
4.  Exécutez Cleanup.bat.  
  
## <a name="see-also"></a>Voir aussi  
 [Orchestrations (dossier d’exemples BizTalk Server)](../core/orchestrations-biztalk-server-samples-folder.md)