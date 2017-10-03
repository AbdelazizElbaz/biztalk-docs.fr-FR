---
title: "Composé du processeur de messages (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, examples
- messages, processing
- messages, aggregated
- examples, pipelines
ms.assetid: a0f87f98-6f5f-4edb-8f65-49d22df5de97
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3853a5b903215b6f716a13c33727e60c67107b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="composed-message-processor-biztalk-server-sample"></a>Traitement des messages composés (exemple BizTalk Server)
Cet exemple a pour but de créer une application de traitement des messages composés qui traite les éléments de ligne individuels à partir de messages agrégés.  
  
 Plus précisément, nous allons créer une planification d'orchestration qui :  
  
1.  Reçoit un message d'échange par lot composé de plusieurs bons de commande.  
  
2.  Désassemble le message d'échange en documents de bon de commande individuels.  
  
3.  Traite chaque document – convertit chaque bon de commande en message de facture.  
  
4.  Assemble tous les messages de facture en un échange par lot.  
  
 L'étape n°3 est simplifiée pour les besoins de l'exemple. Ainsi, dans des applications plus complexes, une orchestration peut envoyer des bons de commande désassemblés à différents systèmes d'inventaire principaux, collecte toutes les réponses, puis les regroupe dans un message de facture par lot.  
  
 Pour plus d'informations sur le modèle de traitement des messages composés, consultez la rubrique [1].  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 La solution de l'exemple est composée de deux projets qui sont détaillés dans les sections suivantes.  
  
### <a name="pipelines-and-schemas"></a>Pipelines et schémas  
 Le projet Pipelines et schémas contient :  
  
-   Des schémas de fichier plat pour l'échange de bon de commande d'entrée et l'échange de facture de sortie.  
  
-   Un mappage pour transformer le document de bon de commande en un document de facture.  
  
-   Des pipelines de réception et d'envoi.  
  
#### <a name="flat-file-schemas-for-input-and-output-interchanges"></a>Schémas de fichier plat pour les échanges d'entrée et de sortie  
 Notre exemple d'application fonctionne avec les échanges dans le format de fichier plat. Voici les exemples d'échange de bon de commande et d'échange de facture :  
  
 Échange de bon de commande (CMPInput.txt) :  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
PO1999-10-21  
US    John Dow       123 Elm Street      Mill Valley    CA 90952  
US    July Dow       8 Pine Avenue       Old Town       PA 95819  
Please ship it urgent!  
ITEMS,ITEM398-BB|Tire|4|324.99|Wrap them up nicely,ITEM201-BB|Engine Oil|1|12.99|SAE10W30|1999-05-22  
PO1999-10-23  
US    John Connor    123 Cedar Street    Mill Valley    CA 90952  
US    Sarah Connor   8 Grass Avenue      Old Town       PA 95819  
Use cheapest shipping method.  
ITEMS,ITEM101-TT|Plastic flowers|10|4.99|Fragile handle with care,ITEM202-RR|Fertilizer|1|10.99|Lawn fertilizer,ITEM453-XS|Weed killer|1|5.99|Lawn weed killer|1999-05-25  
```  
  
 L'échange, ou document de bon de commande, a un en-tête qui identifie le type des documents qu'il contient :  
  
```  
Northwind Shipping  
Batch type:Purchase Orders  
```  
  
 Cet échange est constitué de trois documents de bon de commande. Une seule instance regroupe les informations ci-après. Comme vous pouvez le constater, elle contient des informations telles que l'adresse de facturation et de livraison, ainsi que la liste des articles commandés.  
  
```  
PO1999-10-20  
US    Alice Smith    123 Maple Street    Mill Valley    CA 90952  
US    Robert Smith   8 Oak Avenue        Old Town       PA 95819  
Hurry, my lawn is going wild!  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Confirm this is electric,ITEM926-AA|Baby Monitor|1|39.98|Confirm this is electric|1999-10-21  
```  
  
 L'échange de facture que nous voulons générer pour cela doit ressembler à ceci :  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
INVOICE1999-10-21  
BILLTO,US,John Dow,123 Elm Street,Mill Valley,CA,90952  
398-BB    Tire              4    324.99    Wrap them up nicely  
201-BB    Engine Oil        1    12.99     SAE10W30  
INVOICE1999-10-20  
BILLTO,US,John Connor,123 Cedar Street,Mill Valley,CA,90952  
101-TT    Plastic flowers   10   4.99      Fragile handle with care  
202-RR    Fertilizer        1    10.99     Lawn fertilizer  
453-XS    Weed killer       1    5.99      Lawn weed killer  
```  
  
 Cet échange contient un sous-ensemble d'informations présent dans l'échange de bon de commande. Par ailleurs, le format de l'échange est différent de celui de l'en-tête.  
  
 L'en-tête est le suivant :  
  
```  
Northwest Shipping  
DocumentTypes:Invoices  
```  
  
 L'instance de document inclut les éléments suivants :  
  
```  
INVOICE1999-10-20  
BILLTO,US,Alice Smith,123 Maple Street,Mill Valley,CA,90952  
872-AA    Lawnmower         1    148.95    Confirm this is electric  
926-AA    Baby Monitor      1    39.98     Confirm this is electric  
```  
  
 Tout d'abord, nous devons créer des schémas de fichier plat pour :  
  
-   le document de bon de commande (PO.xsd)  
  
-   le document de facture (Invoice.xsd)  
  
-   l'en-tête du bon de commande (POHeader.xsd)  
  
-   l'en-tête de la facture (InvoiceHeader.xsd)  
  
 Dans le cadre de cet exemple, nous n'allons pas expliquer comment créer des schémas de fichier plat. Pour plus d'informations sur la création de schémas de fichier plat à partir d'instances de document, consultez la section « Création de schémas de fichier plat à partir d'une instance de document » de la documentation.  
  
#### <a name="map-to-transform-purchase-order-document-into-invoice-document"></a>Mappage pour transformer le document de bon de commande en document de facture  
 Le mappage (PO2Invoice.btm) transforme une instance du bon de commande en un document de facture.  
  
#### <a name="receive-and-send-pipelines"></a>Pipelines de réception et d'envoi  
 Le pipeline de réception (FFReceivePipeline.btp) contient un composant Désassembleur de fichier plat utilisé pour traiter un échange de bon de commande. En particulier, pour l'échange dans le fichier CMPInput.txt, il supprime l'en-tête d'échange et produit trois documents XML correspondant aux trois bons de commande.  
  
 Le Désassembleur de fichier plat dans le pipeline de réception est configuré comme suit :  
  
-   **Schéma de document :** PipelinesAndSchemas.PO  
  
-   **Schéma d’en-tête :** PipelinesAndSchemas.POHeader  
  
-   **Préserver l’en-tête :** False  
  
-   **Des échanges récupérables :** False  
  
-   **Schéma de code de fin :** (aucun)  
  
-   **Valider la structure du document :** False  
  
 Le pipeline d'envoi (FFSendPipeline.btp) contient un composant Assembleur de fichier plat utilisé pour créer un échange de facture agrégé.  
  
 L'Assembleur de fichier plat dans le pipeline d'envoi est configuré comme suit :  
  
-   **Schéma de document :** PipelinesandSchemas.Invoice  
  
-   **Schéma d’en-tête :** PipelinesAndSchemas.InvoiceHeader  
  
-   **Conserver la marque d’ordre d’octet :** False  
  
-   **Cible du jeu de caractères :** (aucun)  
  
-   **Schéma de code de fin :** (aucun)  
  
### <a name="orchestration-schedule"></a>Planification d'orchestration  
 La planification d'orchestration (CMP.odx) centralise tout le traitement principal. Plus précisément, les opérations suivantes sont effectuées :  
  
-   Le pipeline de réception est exécuté pour désassembler l'échange de bon de commande.  
  
-   Chaque message de sortie du pipeline de réception est transformé.  
  
-   Le pipeline d'envoi est exécuté pour assembler un échange de facture.  
  
#### <a name="creating-orchestration-schedule-and-defining-global-variables"></a>Création d'une planification d'orchestration et définition des variables globales  
 Notre orchestration reçoit un échange de fichier plat en tant qu'entrée et envoie un échange de fichier plat en tant que sortie. Nous devons donc définir des messages d'entrée et de sortie (nommés respectivement InputInterchange et OutputInterchange) indépendants de tout type (par exemple, de type System.Xml.XmlDocument).  
  
 En outre, nous devons définir une étendue atomique sur laquelle nous traiterons les messages. Cela est nécessaire car le pipeline de réception peut être exécuté au sein de l'étendue atomique.  
  
#### <a name="executing-receive-pipeline"></a>Exécution du pipeline de réception  
 Maintenant, nous allons ajouter une logique pour exécuter un pipeline de réception pour le message reçu dans l'orchestration. Pour ce faire, commençons par déclarer une variable (nommée RcvPipeOutput) de type Microsoft.XLANGs.Pipeline.ReceivePipelineOutputMessages au sein de l'étendue. Cette variable est un énumérateur qui nous permet un cycle dans les messages de sortie du pipeline de réception. Notez que pour accéder à ce type, ainsi qu'à tous les autres types d'exécution des pipelines à partir d'une orchestration, vous devez ajouter des références aux assemblys suivants :  
  
-   Microsoft.XLANGs.Pipeline.dll  
  
-   Microsoft.BizTalk.Pipeline.dll  
  
 Il n'y a aucune garantie que le pipeline de réception s'exécute toujours avec succès. Des messages peuvent parfois être malformés, ce qui provoque l'échec du traitement du pipeline. Lorsque l'exécution d'un pipeline échoue dans l'orchestration, une exception pouvant être interceptée est générée et la logique de gestion des erreurs peut s'appliquer. Afin d'intercepter l'exception générée par le pipeline, nous devons exécuter le pipeline au sein d'une étendue non atomique, avec une gestion des exceptions. Le code réel pour exécuter le pipeline est appelé à partir d'une forme Expression au sein de cette étendue.  
  
 Dans la forme Expression ExecuteRcvPipe, écrivez la ligne de code suivante pour exécuter le pipeline de réception :  
  
```  
RcvPipeOutput = Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteReceivePipeline(typeof(PipelinesAndSchemas.FFReceivePipeline), InputInterchange);  
```  
  
 Analysons cette ligne de code de plus près. Comme vous pouvez le voir, nous appelons une méthode statique ExecuteReceivePipeline qui prend comme paramètre un type de pipeline de réception à exécuter et un message d'entrée. Elle produit alors un objet énumérateur avec l'ensemble des messages de sortie. Le résultat est attribué à une variable de type ReceivePipelineOutputMessages précédemment définie dans cette étendue.  
  
 Nous avons également inclus un bloc de gestion des exceptions pour l'étendue d'exécution du pipeline. Ce bloc intercepte l'exception de type XLANGPipelineManagerException, puis, pour des raisons de simplicité, termine une instance d'orchestration avec un message d'erreur personnalisé.  
  
 Dans des cas plus complexes, une gestion des erreurs supplémentaire peut être effectuée ici, comme la génération du message de notification d'erreur et son envoi par courrier électronique à un utilisateur ou un administrateur des activités.  
  
#### <a name="transforming-pipeline-output-messages"></a>Transformation des messages de sortie du pipeline  
 Une fois que le pipeline a été exécuté et que l'ensemble de messages désassemblés a été produit, nous devons convertir chaque message de sortie dans un format différent.  
  
 Pour utiliser la transformation dans l'orchestration, nous devons définir deux messages : messages d'entrée et de sortie de transformation. Nous allons définir ces messages au sein de l'étendue atomique. Le message d'entrée de transformation, nommé TmpMessageIn, est de type PipelinesAndSchemas.PO. Le message de sortie de transformation, nommé TmpMessageOut, est de type PipelinesAndSchemas.Invoice. Nous allons appliquer le mappage PO2Invoice.btm défini dans le projet PipelinesAndSchemas.  
  
 Comme nous voulons mapper chaque message de sortie du pipeline, nous devons effectuer la transformation dans la boucle. Nous allons utiliser une forme Boucle avec la condition de sortie suivante :  
  
```  
RcvPipeOutput.MoveNext()  
```  
  
 La méthode MoveNext() est une méthode standard de l'interface .NET IEnumerator qui autorise le déplacement au sein de la collection de messages de sortie du pipeline. Lorsqu'elle atteint la fin de la collection, elle renvoie false.  
  
 La première forme Construire sert à créer un message d'orchestration TmpMessageIn à partir du message de sortie du pipeline.  
  
 Le code dans la forme Construction est le suivant :  
  
```  
TmpMessageIn = null;  
RcvPipeOutput.GetCurrent(TmpMessageIn);  
```  
  
 Dans ce code, nous initialisons le message d'orchestration sur null, puis le définissons sur le message actuel à partir de la collection de messages de sortie du pipeline.  
  
 Dans la seconde forme Construire, la transformation réelle de TmpMessageIn est effectuée et le message TmpMessageOut de type PipelinesAndSchemas.Invoice est créé.  
  
#### <a name="executing-send-pipeline"></a>Exécution du pipeline d'envoi  
 La dernière étape de traitement dans l'orchestration consiste à exécuter le pipeline d'envoi de fichier plat pour assembler tous les messages XML transformés en un seul échange de fichier plat.  
  
 Afin d'exécuter un pipeline d'envoi, nous devons utiliser une variable de type Microsoft.XLANGs.Pipeline.SendPipelineInputMessages, nommée SendPipeInput, qui contient une collection de messages d'orchestration devant être traitée dans un pipeline d'envoi.  
  
 Dans la dernière expression de la boucle où nous avons effectué la transformation, nous allons écrire un code qui ajoute chaque message transformé à une collection de messages pour le pipeline d'envoi :  
  
```  
SendPipeInput.Add(TmpMessageOut);  
```  
  
 Comme pour l'exécution du pipeline de réception, le code pour l'exécution du pipeline d'envoi est placé dans une étendue non atomique avec un bloc de gestion des exceptions. Le code d'exécution du pipeline d'envoi se trouve dans la forme Assignation de message du bloc de construction.  
  
```  
OutputInterchange = null;  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(typeof(PipelinesAndSchemas.FFSendPipeline), SendPipeInput, OutputInterchange);  
```  
  
 Le bloc de construction est utilisé pour créer le message de sortie du pipeline OutputInterchange, indépendant de tout type (par exemple, System.Xml.XmlDocument). Puis, dans la forme Assignation de message, le message nouvellement construit est initialisé sur null. Ensuite, la méthode statique ExecuteSendPipeline est appelée pour exécuter un pipeline d'envoi. Cette méthode prend comme paramètre un type de pipeline d'envoi à exécuter, le message d'entrée et la référence au message de sortie dans lequel la sortie du pipeline sera stockée.  
  
 Comme pour l'exécution du pipeline de réception, nous avons ici aussi un bloc de gestion des exceptions pour l'étendue d'exécution du pipeline. Ce bloc intercepte l'exception de type XLANGPipelineManagerException, puis, pour des raisons de simplicité, termine une instance d'orchestration avec un message d'erreur personnalisé.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Le tableau suivant répertorie les fichiers de cet exemple.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC).<br /><br /> Supprime les ports d'envoi et de réception.<br /><br /> Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|ComposedMessageProcessor.sln|Fichier de solution Visual Studio pour l'exemple.|  
|ComposedMessageProcessorBinding.xml|Fichier de liaison pour l'exemple.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Dans le dossier Orchestration :<br /><br /> CMP.odx|Orchestration qui exécute le pipeline de réception pour désassembler le message, transforme chaque message désassemblé, puis exécute le pipeline d'envoi pour assembler des messages dans un échange.|  
|Dans le dossier Orchestration :<br /><br /> Orchestration.btproj|Projet BizTalk pour l'orchestration.|  
|Dans le dossier Orchestration :<br /><br /> SuspendMessage.odx|Orchestration utilisée pour interrompre les messages dont le traitement du pipeline échoue.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> CMPInput.xml, CMPOutput.xml|Instances de document d'entrée et de sortie pour l'exemple.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> FFReceivePipeline.btp, FFSendPipeline.btp|Pipelines de réception et d'envoi avec des composants de fichier plat. Ces pipelines sont exécutés au sein de l'orchestration.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> Invoice.xsd, InvoiceHeader.xsd|Schémas de fichier plat pour le document et l'en-tête de sortie.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> PO.xsd, POHeader.xsd|Schémas de fichier plat pour le document et l'en-tête d'entrée.|  
|Dans le dossier PipelinesAndSchemas :<br /><br /> PropertySchema.xsd|Schéma de propriété pour l'exemple.|  
  
## <a name="building-and-initializing-the-sample"></a>Création et initialisation de l'exemple  
 La procédure suivante permet de créer et d'initialiser l'exemple Compose.  
  
#### <a name="to-build-and-initialize-the-compose-sample"></a>Pour créer et initialiser l'exemple Compose  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<Exemples de chemin d’accès > \Pipelines\ComposedMessageProcessor  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier :  
  
         \<Exemples de chemin d’accès > \Pipelines\ComposedMessageProcessor  
  
    -   Compilation des projets Visual Studio pour cet exemple.  
  
    -   Création d'une application appelée « CMP Sample » et déploiement des assemblys de l'exemple au sein de celle-ci.  
  
    -   Création et liaison de l'emplacement de réception de BizTalk Server, ainsi que des ports d'envoi et de réception.  
  
    -   Inscription et démarrage de l'orchestration, activation de l'emplacement de réception et démarrage du port d'envoi.  
  
         Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe). Utilisez cette paire de clés pour signer les assemblys obtenus.  
  
3.  Avant de tenter d'exécuter cet exemple, vous devez vérifier que BizTalk Server n'a pas signalé d'erreur durant le processus de création et d'initialisation.  
  
     Pour annuler les modifications apportées par Setup.bat, vous devez effectuer les opérations suivantes :  
  
    1.  Arrêtez et redémarrez l'instance de l'hôte à partir de la console Administration de BizTalk Server.  
  
    2.  Exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
 La procédure suivante permet d'exécuter l'exemple ComposedMessageProcessor.  
  
#### <a name="to-run-the-composedmessageprocessor-sample"></a>Pour exécuter l'exemple ComposedMessageProcessor  
  
1.  Copiez le fichier texte CMPInput.txt situé dans le dossier PipelinesAndSchemas. Collez le fichier dans le dossier In.  
  
2.  Observez le fichier texte créé dans le dossier Out. Ce fichier contient les mêmes enregistrements que CMPInput.txt, mais le format des données dans le fichier est différent.  
  
     Quand le message transite par BizTalk Server, les événements suivants se produisent :  
  
    1.  Le message est désassemblé et converti en messages XML. Chaque message est mappé à un format différent.  
  
    2.  Tous les messages mappés sont assemblés et convertis au format de fichier plat.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipelines (dossier d’exemples BizTalk Server)](../core/pipelines-biztalk-server-samples-folder.md)