---
title: "Types de données dans la carte de base de données Oracle de diffusion en continu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- streaming, support in the WCF service model
- streaming, support for
- streaming, support in BizTalk Server
- streaming, support in the WCF channel model
ms.assetid: c6cbe870-6794-4bf1-90c1-db65a242e8fe
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fda4d99eb381321139e4ed493f119f9eaf21623e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="streaming-large-object-data-types-in-oracle-database-adapter"></a>Diffusion en continu des types de données dans la carte de base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge la diffusion en continu pour les types de données Oracle LOB (large object). Avec la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] opérations sont appelées et les réponses sont retournées en échangeant des messages SOAP. Un corps de message SOAP est composé de nœuds XML.  
  
 Il existe deux types de messages de diffusion en continu sont pris en charge par l’adaptateur :  
  
-   **Nœud de diffusion en continu**. Dans le nœud de diffusion en continu de chaque nœud est mis en mémoire tampon par l’adaptateur avant d’être envoyée à la base de données Oracle (ou retournée au client). Cela signifie que, pour un type de données LOB, la valeur entière est en lecture dans une mémoire tampon.  
  
-   **Diffusion en continu de la valeur du nœud**. Dans valeur de nœud de diffusion en continu de la valeur réelle du nœud peut être diffusée en segments entre la base de données Oracle et le client. Diffusion en continu de la valeur du nœud prend en charge la diffusion en continu de bout en bout des types de données LOB entre le client de carte et de la base de données Oracle.  
  
 Les deux de ces modes de diffusion en continu s’appuient sur la prise en charge pour le nœud de diffusion en continu et la valeur du nœud de diffusion en continu sur les messages dans WCF. Pour cette raison, diffusion en continu pour les types LOB dépend étroitement comment les messages sont créés et consommées par l’adaptateur et par une application cliente. Une conséquence de cela est que la prise en charge pour les types LOB de diffusion en continu n’est pas le même sur tous les modèles de programmation.  
  
 Les sections de cette rubrique fournissent :  
  
-   Informations fondamentales sur la prise en charge des messages de diffusion en continu dans WCF et comment il est implémenté par l’adaptateur.  
  
-   Informations sur la diffusion en continu pour les types de données LOB comment est pris en charge lorsque vous utilisez l’adaptateur dans chaque modèle de programmation.  
  
## <a name="streaming-fundamentals"></a>Notions de base de diffusion en continu  
 La prise en charge pour la diffusion implémentée par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une combinaison de :  
  
-   Prise en charge de la diffusion en continu message dans WCF.  
  
-   Diffusion en continu de la prise en charge dans la bibliothèque du client Oracle (ODP.NET).  
  
-   Les façon dont les messages sont créés et consommés en interne par l’adaptateur.  
  
### <a name="message-streaming-support-in-wcf"></a>Prise en charge des messages de diffusion en continu dans WCF  
 Comment WCF prend en charge la diffusion en continu sur un message dépend à la fois sur la façon dont le message est créé et comment le message est utilisé.  
  
-   Un message WCF est créé à l’aide de la méthode statique **créer** méthode **System.ServiceModel.Channels.Message**. Cette méthode a plusieurs surcharges qui prennent en charge de différentes façons de passer le corps du message. Un message WCF peut être créé en passant le corps de message à l’aide de :  
  
    -   A **System.Xml.XmlReader**, ou  
  
    -   A **System.ServiceModel.Channels.BodyWriter**.  
  
-   Un message WCF peut être consommé à l’aide de  
  
    -   Un **XmlReader** en appelant **Message.GetReaderAtBodyContents()**, ou  
  
    -   Un **XmlDictionaryWriter** en appelant **Message.WriteBodyContents(XmlDictionaryWriter)**.  
  
 Le tableau suivant montre comment se comporte de WCF pour différentes combinaisons de la création et la consommation des messages.  
  
|Message créé avec|Message consommée avec|Comportement WCF|  
|--------------------------|---------------------------|------------------|  
|**XmlBodyWriter**|**XmlDictionaryWriter**|**Valeur de nœud de diffusion en continu** est pris en charge. WCF dirige les deux enregistreurs pour activer la diffusion en continu. Les deux le **XmlBodyWriter** et **XmlDictionaryWriter** doit prendre en charge les valeur du nœud de diffusion en continu pour qu’il puisse se produire.|  
|**XmlBodyWriter**|**XmlReader**|**Nœud de diffusion en continu** est pris en charge. WCF met en mémoire tampon en interne le **XmlReader**.|  
|**XmlReader**|**XmlDictionaryWriter**|**Nœud de diffusion en continu** est pris en charge. WCF met en mémoire tampon en interne le **XmlReader** et rappelle le **XmlDictionaryWriter**.|  
|**XmlReader**|**XmlReader**|**Nœud de diffusion en continu** est pris en charge. WCF met en mémoire tampon en interne le **XmlReader**.|  
  
### <a name="streaming-support-in-the-oracle-client-library-odpnet"></a>Prise en charge de diffusion en continu dans la bibliothèque du Client Oracle (ODP.NET)  
 ODP.NET prend en charge la diffusion en continu de la manière suivante :  
  
-   Diffusion en continu est prise en charge uniquement sur les types de données Oracle LOB.  
  
-   Pour certaines opérations de table (et de vue), les types de données LOB sont en mémoire tampon. Par conséquent, il n’est possible d’aucune diffusion en continu.  
  
### <a name="internal-message-handling-by-the-adapter"></a>Gestion des messages interne par l’adaptateur  
 L’adaptateur prend en charge la diffusion en continu de la manière suivante :  
  
-   L’adaptateur étend **Message** d’implémenter une classe de message personnalisé, **Microsoft.Adapters.AdapterUtilities.AdapterMessage**. Il crée un **AdapterMessage** de WCF tous les messages elle fournit au client de carte ; Cela inclut les messages de réponse pour toutes les opérations sortants et le message de demande pour l’opération POLLINGSTMT. Cela permet à la carte prendre en charge de la valeur du nœud de diffusion en continu pour l’opération ReadLOB en fournissant une **XmlReader** qui prend en charge **ReadValueChunk** aux clients de la carte.  
  
-   L’adaptateur utilise tous les messages reçus à partir du client à l’aide d’une implémentation personnalisée de **XmlDictionaryWriter**.  
  
-   L’adaptateur crée tous les messages qu’il envoie au client à l’aide d’une implémentation personnalisée de **XmlBodyWriter**, à l’exception du message de réponse ReadLOB. (Cela inclut les messages de réponse pour toutes les opérations sortants et le message de demande pour l’opération POLLINGSTMT).  
  
## <a name="streaming-support-in-the-wcf-channel-model"></a>Prise en charge de diffusion en continu dans le modèle de canal WCF  
 Le tableau suivant fournit des informations détaillées sur la diffusion en continu est prise en charge dans le modèle de canal WCF.  
  
|Opération|Nœud de diffusion en continu|Valeur du nœud de diffusion en continu| Description|  
|---------------|--------------------|---------------------------|-----------------|  
|L’opération d’insertion de la table|Pris en charge*|Non pris en charge entre l’adaptateur et la base de données Oracle. Prise en charge entre le client et le adapter.*|Nœud de bout en bout-valeur de diffusion en continu n’est pas pris en charge, car les valeurs des colonnes LOB sont mis en mémoire tampon par ODP.NET et l’insertion est alors effectuée. Toutefois, entre le client et l’adaptateur de diffusion en continu de valeur de nœud est possible pour les colonnes LOB, si le client crée le message avec un **BodyWriter**.|  
|Opération de sélection de table|Pris en charge|Pris en charge|L’adaptateur utilise un **BodyWriter** pour créer le message de réponse. Si le client utilise le message en utilisant un **XmlDictionaryWriter**, diffusion en continu pour les colonnes LOB-valeur du nœud se produit.|  
|Opération de mise à jour de table|Pris en charge|Non pris en charge entre l’adaptateur et la base de données Oracle. Prise en charge entre le client et l’adaptateur.|Nœud de bout en bout-valeur de diffusion en continu n’est pas pris en charge, car les valeurs des colonnes LOB sont mis en mémoire tampon par ODP.NET et, la mise à jour est effectuée. Toutefois, entre le client et l’adaptateur de diffusion en continu de valeur de nœud est possible pour les colonnes LOB si le client crée le message avec un **BodyWriter**.|  
|Opération de suppression de table|Pris en charge|Non pris en charge entre l’adaptateur et la base de données Oracle. Prise en charge entre le client et l’adaptateur.|Nœud de bout en bout-valeur de diffusion en continu n’est pas pris en charge, car les valeurs des colonnes LOB sont mis en mémoire tampon par ODP.NET et la suppression est alors effectuée. Toutefois, entre le client et l’adaptateur de diffusion en continu de valeur de nœud est possible pour les colonnes LOB si le client crée le message avec un **BodyWriter**.|  
|Opération de table ReadLOB|Pris en charge|Pris en charge|L’opération ReadLOB est principalement conçue pour les colonnes de données LOB de flux de données dans le modèle de service WCF. Dans le modèle de canal WCF, si le client utilise le message à l’aide un **XmlReader** (en appelant le **GetReaderAtBodyContents** méthode sur le message de réponse), valeur de nœud de bout en bout de diffusion en continu se produit. Il s’agit, car l’adaptateur retourne un **XmlReader** qui prend en charge **ReadValueChunk** appelle pour le message de réponse ReadLOB. Toutefois, il est recommandé de ne pas utiliser l’opération ReadLOB à partir du modèle de canal WCF. Vous pouvez utiliser une opération de sélection ou d’une opération SQLEXECUTE à la place.|  
|Opération de table UpdateLOB|Pris en charge|Pris en charge|L’adaptateur utilise un **XmlDictionaryWriter** pour consommer le message de demande. Si le client utilise un **BodyWriter** pour créer le message de demande, le nœud-valeur de bout en bout pour les données LOB de diffusion en continu se produit.|  
|Opération SQLEXECUTE|Pris en charge|Pris en charge|L’adaptateur utilise un **BodyWriter** pour créer le message de réponse.<br /><br /> Si le client utilise un **XmlDictionaryWriter** pour consommer le message de réponse, le nœud-valeur de bout en bout pour les données LOB de diffusion en continu se produit.<br /><br /> Nœud de bout en bout-valeur de diffusion en continu n’est pas prise en charge pour le message de demande, car l’adaptateur doit mettre en mémoire tampon tous les opérandes avant qu’il peut appeler l’opération sur la base de données Oracle.|  
|Opération de procédure et la fonction stockée|Pris en charge|Pris en charge|L’adaptateur utilise un **BodyWriter** pour créer le message de réponse.<br /><br /> Si le client utilise un **XmlDictionaryWriter** pour consommer le message de réponse, le nœud-valeur de bout en bout pour les données LOB de diffusion en continu se produit. (Cela signifie que de diffusion en continu est prise en charge pour la sortie et en procédure et la fonction de paramètres OUT dans le message de réponse.)<br /><br /> Nœud de bout en bout-valeur de diffusion en continu n’est pas prise en charge pour le message de demande, car l’adaptateur doit mettre en mémoire tampon tous les opérandes avant qu’il peut appeler l’opération sur la base de données Oracle.|  
|Opération de POLLINGSTMT|Pris en charge|Pris en charge|L’adaptateur utilise un **BodyWriter** pour créer le message de demande POLLINGSTMT. Si le client utilise le message en utilisant un **XmlDictionaryWriter**, puis de la valeur du nœud de diffusion en continu pour les colonnes LOB se produit.|  
  
 Pour plus d’informations sur l’implémentation des données LOB de diffusion en continu dans votre code lorsque vous utilisez le modèle de canal WCF, consultez [de diffusion en continu Oracle de base de données LOB données Types à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).  
  
## <a name="streaming-support-in-the-wcf-service-model"></a>Prise en charge de diffusion en continu dans le modèle de Service WCF  
 Sérialisation et la désérialisation entre la représentation XML d’un message et la représentation d’objet de code managé de ce message requièrent l’écriture et de la lecture de la totalité du message en mémoire. Pour cette raison, nœud de diffusion en continu, ni diffusion en continu de valeur de nœud est pris en charge pour la plupart des opérations.  
  
 La seule exception à cela est l’opération ReadLOB. Cette opération est implémentée spécifiquement pour prendre en charge la diffusion en continu de bout en bout pour la lecture de table et vue des colonnes LOB dans le modèle de service WCF.  
  
## <a name="streaming-support-in-biztalk-server"></a>Prise en charge de diffusion en continu dans BizTalk Server  
 Le tableau suivant fournit des informations détaillées sur la diffusion en continu est prise en charge dans BizTalk Server. (Toutes les références à « carte » font référence à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; l’adaptateur WCF-Custom est toujours référencée par son nom complet dans ce tableau.)  
  
|Opération|Nœud de diffusion en continu|Valeur du nœud de diffusion en continu| Description|  
|---------------|--------------------|---------------------------|-----------------|  
|L’opération d’insertion de la table|Pris en charge*|Non pris en charge entre l’adaptateur et la base de données Oracle ; Toutefois, les données sont transmis en continu entre BizTalk Server et de la carte.|Nœud de bout en bout-valeur de diffusion en continu n’est pas pris en charge, car les valeurs des colonnes LOB sont mis en mémoire tampon par ODP.NET et l’insertion est alors effectuée. Toutefois, diffusion en continu entre BizTalk Server et de l’adaptateur de valeur de nœud est pris en charge pour les types de données LOB, car l’adaptateur WCF-Custom crée le message avec un **BodyWriter**.|  
|Opération de sélection de table|Pris en charge|Pris en charge|L’adaptateur WCF-Custom utilise un **XmlDictionaryWriter** pour consommer le message de réponse, afin de bout en bout-valeur de nœud de diffusion en continu pour les types LOB est pris en charge.|  
|Opération de mise à jour de table|Pris en charge|Non pris en charge entre l’adaptateur et la base de données Oracle ; Toutefois, les données sont transmis en continu entre BizTalk Server et de la carte.|Nœud de bout en bout-valeur de diffusion en continu n’est pas pris en charge, car les valeurs des colonnes LOB sont mis en mémoire tampon par ODP.NET et, la mise à jour est effectuée. Toutefois, diffusion en continu entre BizTalk Server et de l’adaptateur de valeur de nœud est pris en charge pour les types de données LOB, car l’adaptateur WCF-Custom crée le message avec un **BodyWriter**.|  
|Opération de suppression de table|Pris en charge|Non pris en charge entre l’adaptateur et la base de données Oracle ; Toutefois, les données sont transmis en continu entre BizTalk Server et de la carte.|Nœud de bout en bout-valeur de diffusion en continu n’est pas pris en charge, car les valeurs des colonnes LOB sont mis en mémoire tampon par ODP.NET et la suppression est alors effectuée. Toutefois, diffusion en continu entre BizTalk Server et de l’adaptateur de valeur de nœud est pris en charge pour les types de données LOB, car l’adaptateur WCF-Custom crée le message avec un **BodyWriter**.|  
|Opération de table ReadLOB|L’opération ReadLOB n’est pas prise en charge pour BizTalk Server.|L’opération ReadLOB n’est pas prise en charge pour BizTalk Server.|L’opération ReadLOB n’est pas prise en charge pour BizTalk Server. Utilisez plutôt l’opération Select ou une opération SQLEXECUTE.|  
|Opération de table UpdateLOB|Pris en charge|Pris en charge|L’adaptateur WCF-Custom utilise un **BodyWriter** pour créer le message de demande, de bout en bout-valeur de nœud de diffusion en continu pour les types de données LOB est prise en charge.|  
|Opération SQLEXECUTE|Pris en charge|Pris en charge|L’adaptateur WCF-Custom utilise un **XmlDictionaryWriter** pour consommer le message de réponse, donc la prise en charge de bout en bout-valeur de nœud de diffusion en continu pour les types de données LOB dans le message de réponse.<br /><br /> Nœud de bout en bout-valeur de diffusion en continu n’est pas prise en charge pour le message de demande, car l’adaptateur doit mettre en mémoire tampon tous les opérandes avant qu’il peut appeler l’opération sur la base de données Oracle.|  
|Opération de procédure et la fonction stockée|Pris en charge|Pris en charge|L’adaptateur WCF-Custom utilise un **XmlDictionaryWriter** pour consommer le message de réponse, donc la prise en charge de bout en bout-valeur de nœud de diffusion en continu pour les types de données LOB dans le message de réponse. (Cela signifie que de diffusion en continu est prise en charge pour la sortie et en procédure et la fonction de paramètres OUT dans le message de réponse.)<br /><br /> Nœud de bout en bout-valeur de diffusion en continu n’est pas prise en charge pour le message de demande, car l’adaptateur doit mettre en mémoire tampon tous les opérandes avant qu’il peut appeler l’opération sur la base de données Oracle.|  
|Opération de POLLINGSTMT|Pris en charge|Pris en charge|L’adaptateur WCF-Custom utilise un **XmlDictionaryWriter** pour consommer le message de demande (entrant), afin de bout en bout-valeur de nœud de diffusion en continu pour les types de données LOB est pris en charge.|  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)