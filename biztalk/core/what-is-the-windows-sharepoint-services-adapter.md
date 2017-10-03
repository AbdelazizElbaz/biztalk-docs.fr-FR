---
title: "Qu'est-ce que l'adaptateur Windows SharePoint Services ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, process flow
- Windows SharePoint Services adapters, receiving documents
- Windows SharePoint Services adapters, sending documents
- Windows SharePoint Services adapters, security
- Windows SharePoint Services adapters
- Windows SharePoint Services adapters, about Windows SharePoint Services adapters
ms.assetid: 1875ac85-46c2-4da5-ad16-8b078cb4cbd7
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a25bc378bdbb4c8bef34c3cff0140d03094faad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-windows-sharepoint-services-adapter"></a>Qu'est-ce que l'adaptateur Windows SharePoint Services ?
L'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Windows SharePoint Services fournit une intégration étroite avec Windows SharePoint Services et Microsoft Office InfoPath. La rubrique suivante décrit les fonctionnalités et le fonctionnement de l'adaptateur Windows SharePoint Services.  
  
## <a name="features-of-the-windows-sharepoint-services-adapter"></a>Fonctionnalités de l'adaptateur Windows SharePoint Services  
 La liste suivante décrit les fonctionnalités importantes de l'adaptateur Windows SharePoint Services :  
  
-   Possibilité d'envoyer des messages XML et binaires BizTalk Server aux bibliothèques de documents SharePoint.  
  
-   Intégration avec InfoPath : vous pouvez transformer les messages sortants de BizTalk Server XML s’ouvre automatiquement dans InfoPath lorsqu’ils sont ouverts à partir du site Windows SharePoint Services.  
  
-   Promotion des propriétés pour les messages vers Windows SharePoint Services. Jusqu'à 16 colonnes SharePoint peuvent être mises à jour avec les métadonnées BizTalk Server relatives à l'ID d'instance de l'orchestration du message, à l'ID du message ou aux valeurs extraites du message.  
  
-   Définition du nom de fichier basée sur le contenu du message et les propriétés de BizTalk Server.  
  
-   La possibilité d’envoyer des documents à une liste arbitraire (et non à une bibliothèque de documents) : dans ce cas le document lui-même n’est pas stocké dans Windows SharePoint Services, mais la promotion de propriété se produit pour un élément de liste est créé et les valeurs de colonne sont récupérées à partir du message.  
  
-   Possibilité de recevoir des messages depuis n'importe quelle vue de toute bibliothèque de documents et de les archiver dans une bibliothèque de documents spécifiée à l'aide du nom de fichier spécifié.  
  
-   Promotion des propriétés de l’adaptateur Windows SharePoint Services dans BizTalk Server : informations sur les fichiers Windows SharePoint Services sont rendues disponibles dans BizTalk Server en tant que propriétés de contexte de message. Ces dernières sont accessibles à partir des pipelines, des orchestrations, etc. Les colonnes SharePoint personnalisées sont accessibles par l'intermédiaire du document WSS.InPropertiesXml.  
  
-   Prise en charge pour les ports dynamiques complète : envoyer des adaptateurs peuvent prendre en charge (défini par l’utilisateur lors de la création du port d’envoi) de liaison d’URI statique ou dynamique (définie par l’orchestration lors de l’envoi du message). Toutes les informations de configuration peuvent être définies par le biais des propriétés de contexte du message, telles que WSS.Filename et WSS.ConfigTimeout, pour les ports d'envoi dynamiques et les ports d'envoi physiques.  
  
-   Compteurs de performance  
  
## <a name="how-the-windows-sharepoint-services-adapter-works"></a>Fonctionnement de l'adaptateur Windows SharePoint Services  
 L'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Windows SharePoint Services comprend trois composants principaux :  
  
-   Le service Web de l'adaptateur Windows SharePoint Services  
  
-   L'adaptateur de réception Windows SharePoint Services  
  
-   L'adaptateur d'envoi Windows SharePoint Services  
  
 Sur le serveur Windows SharePoint Services, le service Web (BTSharePointAdapterWS.asmx) est installé pour donner accès aux bibliothèques et listes Windows SharePoint Services. Le service Web expose des méthodes pour obtenir, placer, supprimer et archiver des documents dans une bibliothèque SharePoint. L'adaptateur de réception récupère les fichiers du service Web et l'adaptateur d'envoi y publie des fichiers.  
  
 La figure suivante montre les principaux composants de l'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Windows SharePoint Services qui dispose de ces fonctionnalités.  
  
 ![](../core/media/bts-dev-adapters-wss-architecture.gif "BTS_Dev_Adapters_WSS_Architecture")  
  
### <a name="receiving-documents-from-windows-sharepoint-services"></a>Réception de documents à partir de Windows SharePoint Services  
 L'adaptateur de réception interroge les vues des bibliothèques de documents Windows SharePoint Services. Il appelle une méthode Web sur le serveur Windows SharePoint Services qui utilise le modèle d'objet Windows SharePoint Services pour parcourir la bibliothèque, extraire les fichiers et renvoyer les données de fichier à l'adaptateur. Ce dernier envoie ensuite les fichiers à la base de données MessageBox de BizTalk Server et appelle une autre méthode Web pour supprimer ou archiver les fichiers dans Windows SharePoint Services. Afin de filtrer les fichiers dans une bibliothèque Windows SharePoint Services, l'adaptateur interroge la bibliothèque Windows SharePoint Services par le biais d'une vue Windows SharePoint Services.  
  
 L'approche (d'interrogation) centralisée fournit un modèle de gestion simple configuré sur le serveur BizTalk. Elle offre également des performances améliorées du fait de l'autorisation du traitement des messages par lot.  
  
 Comme la prise en charge de la transaction au niveau de la plateforme n'est pas disponible dans Windows SharePoint Services, les services Web et BizTalk Server, le mécanisme d'extraction est utilisé pour minimiser les erreurs associées aux conditions d'échec. Dans certaines conditions (à savoir quand les fichiers sont envoyés avec succès à la base de données MessageBox de BizTalk Server mais ne peuvent pas être supprimés de Windows SharePoint Services), les fichiers restent extraits sur le serveur Windows SharePoint Services même s'ils ont été envoyés à BizTalk Server. Les erreurs sont consignées dans le journal des événements sur le serveur BizTalk.  
  
### <a name="sending-documents-to-windows-sharepoint-services"></a>Envoi de documents à Windows SharePoint Services  
 L'adaptateur envoie des documents à Windows SharePoint Services en appelant une méthode Web sur le serveur Windows SharePoint Services. L'adaptateur spécifie l'URL du site Windows SharePoint Services, la bibliothèque de documents ou l'URL de liste relative au nom du site, du fichier ou de l'élément de liste, ainsi que les propriétés promues à associer au fichier.  
  
 Vous pouvez définir le nom de fichier sur une chaîne fixe ou sur un nom dérivé des données XML dans le document. La dérivation du nom peut être très utile pour appliquer les conventions d'affectation de noms standard. L'adaptateur peut également définir des valeurs de propriétés promues dans le fichier en tant que valeurs de colonne. Comme avec les noms de fichier, les valeurs de propriétés promues peuvent être fixes ou dérivées des données XML dans le document.  
  
> [!IMPORTANT]
>  Les propriétés promues dans l'adaptateur Windows SharePoint Services sont des entités différentes des propriétés promues dans BizTalk Server ou dans Windows SharePoint Services.  
  
 Les propriétés promues dans Windows SharePoint Services servent à rendre visibles les éléments XML lors du parcours d'une bibliothèque de formulaires Windows SharePoint Services. Lorsqu'un formulaire InfoPath est publié dans une bibliothèque de formulaires Windows SharePoint Services, InfoPath configure la bibliothèque de formulaires pour promouvoir les éléments clés, rendant cela automatique. Cette fonctionnalité est disponible dans Windows SharePoint Services uniquement lors de l'utilisation de bibliothèques de formulaires InfoPath (bibliothèques de documents qui stockent des formulaires InfoPath avec les mêmes schéma XSD et solution InfoPath).  
  
 La promotion des propriétés de l'adaptateur Windows SharePoint Services permet à l'utilisateur de promouvoir des propriétés dans Windows SharePoint Services lorsque des documents avec des schémas différents sont stockés dans la même bibliothèque de documents.  
  
 La promotion des propriétés de BizTalk Server est un concept similaire, à ceci près que les propriétés sont rendues visibles pour l'orchestration en tant que propriétés sur le message et non pour l'utilisateur final dans l'interface utilisateur. En outre, BizTalk Server prend en charge un concept de rétrogradation de propriétés lorsque les valeurs de propriété sont enregistrées de nouveau dans le document.  
  
 Lors de l'utilisation de l'adaptateur Windows SharePoint Services avec des formulaires InfoPath et des bibliothèques de formulaires (plutôt que des documents XML arbitraires et des bibliothèques de documents), vous ne devez pas définir les propriétés promues à l'aide de l'adaptateur d'envoi. Au lieu de cela, le document peut être modifié au sein de l'orchestration (directement en modifiant le message ou indirectement par le biais de propriétés rétrogradées). Les valeurs sont automatiquement promues par Windows SharePoint Services.  
  
## <a name="security-considerations-for-the-windows-sharepoint-services-adapter"></a>Considérations relatives à la sécurité pour l'adaptateur Windows SharePoint Services  
 L'adaptateur Windows SharePoint Services comprend des sous-systèmes, le service Web BTSharePointAdapterWS qui s'exécute sur le site Web Windows SharePoint Services et le composant d'exécution de l'adaptateur qui s'exécute sur le serveur BizTalk dans le processus de l'instance de l'hôte BizTalk Server. Le composant d'exécution de l'adaptateur appelle le service Web BTSharePointAdapterWS qui doit disposer des autorisations pour effectuer certaines tâches dans Windows SharePoint Services. Comme ce composant s'exécute en tant qu'appelant, les autorisations doivent être accordées à l'appelant. Cela signifie que l’instance d’hôte BizTalk doit être effectuée une **collaborateur** sur le site SharePoint pour pouvoir envoyer et recevoir des messages à partir de ce site. Le service BTSharePointAdapterWS Web peut être appelé uniquement par les membres de la **hôtes avec SharePoint activé** groupe. Afin de permettre une instance d’hôte BizTalk, l’exécution de l’adaptateur, pour interagir avec le service Web, en cours d’exécution l’instance d’hôte compte Windows doit correspondre à un membre de la **hôtes avec SharePoint activé** groupe. Il s’agit de la responsabilité de l’administrateur pour ajouter et supprimer des comptes dans ce groupe, ainsi que de faire de l’instance d’hôte comptes membres SharePoint **collaborateur** rôle.  
  
|Composant|Identité du processus|Autorisation|  
|---------------|----------------------|----------------|  
|Service Web BTSharePointAdapterWS|Identité de l'appelant|Appeler l'autorisation accordée au groupe Hôtes avec SharePoint activé|  
|Composant d'exécution de l'adaptateur|Identité de l'hôte BizTalk|Néant|  
|Modèle d'objet Windows SharePoint Services|Néant|Le groupe hôtes avec SharePoint activé doit être un membre de la **collaborateur** rôle dans SharePoint Services.|  
  
 Le programme d’installation de BizTalk Server configure les autorisations sur le service BTSharePointAdapterWS Web afin que seuls les comptes qui sont membres de la **hôtes avec SharePoint activé** groupe peut accéder à ce service Web. Si vous souhaitez que les ordinateurs hôtes pour exécuter l’adaptateur Windows SharePoint Services, l’administrateur aura ajouter le groupe NT associé à cet ordinateur hôte de le **hôtes avec SharePoint activé** groupe et ajouter la **hôtes avec SharePoint activé**  groupe Windows SharePoint Services **collaborateur** rôle.  
  
 Les autorisations pour accéder aux fichiers, listes et bibliothèques de documents Windows SharePoint Services sont limitées à l'aide de la sécurité Windows SharePoint Services. Les messages sont envoyés à partir de Windows SharePoint Services directement à BizTalk Server. La communication entre le composant d'exécution de l'adaptateur et le service Web s'effectue via HTTP ou HTTPS.  
  
 L'adaptateur suppose que le service Web BTSharePointAdapterWS utilise le même schéma HTTP (HTTP ou HTTPS) que le site Windows SharePoint Services. Cela signifie que l'adaptateur utilise HTTPS pour communiquer avec le service Web BTSSharePointAdapterWS lorsque le site Windows SharePoint Services est créé sur un site Web IIS sécurisé ou qu'il utilise HTTP pour communiquer avec le service Web BTSharePointAdapterWS lorsque le site Windows SharePoint Services est créé sur un site Web IIS sans certificat de serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration et déploiement de l’adaptateur Windows SharePoint Services](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md)   
 [Configuration de l’adaptateur Windows SharePoint Services](../core/configuring-the-windows-sharepoint-services-adapter.md)   
 [Procédures pas à pas de carte de Windows SharePoint Services](../core/windows-sharepoint-services-adapter-walkthroughs.md)