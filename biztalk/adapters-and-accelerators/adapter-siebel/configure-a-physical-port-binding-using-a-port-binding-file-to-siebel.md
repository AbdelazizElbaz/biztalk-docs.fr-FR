---
title: "Configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port binding file
- physical port binding, configuring by using a port binding file
ms.assetid: 1758e89c-d56c-4e67-919b-c0bbb22878bf
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05bfa8539c223078fd29c5d99cfac50217bbaa36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-physical-port-binding-using-a-port-binding-file-to-siebel"></a>Configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel
Lorsque vous utilisez la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées pour un artefact Siebel, autres que les fichiers de schéma, le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère également un fichier de liaison de port. Vous pouvez importer ce fichier de liaison dans votre application BizTalk pour créer un port d’envoi physiques. Consultez [réutiliser les liaisons de l’adaptateur dans l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md). Si vous importez ce fichier de liaison, vous n’avez pas à créer manuellement un port d’envoi physiques.  
  
> [!IMPORTANT]
>  Lors de l’utilisation du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier de liaison. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier de liaison, si nécessaire.  
  
 Création d’un port à l’aide du fichier de liaison de port de toujours crée un port d’envoi bidirectionnel. Si vous souhaitez créer un port unidirectionnel, vous pouvez le créer manuellement en suivant les étapes indiquées dans [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md). Ou bien, vous pouvez suivre les solutions de contournement décrites dans cette rubrique pour modifier le fichier de liaison de port pour créer des ports unidirectionnels.  
  
> [!IMPORTANT]
>  À l’aide de la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ne crée pas un fichier de liaison de port à l’aide de laquelle vous pouvez créer un port WCF-Siebel. Toutefois, vous pouvez apporter des modifications dans le fichier de liaison de port généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et l’utiliser pour créer un port WCF-Siebel. Pour plus d’informations, voir Configuration d’un Port WCF-Siebel avec le complément, Port de liaison fichier généré à l’aide de Consume Adapter Service.  
  
 Voici quelques points clés que vous devez comprendre en ce qui concerne le fichier de liaison généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]:  
  
-   Les fichiers sont créés avec une convention d’affectation de noms spécifique. Si vous avez généré des métadonnées pour les opérations sortantes, qui consiste à envoyer des messages au système Siebel, le nom du fichier est WcfSendPort_SiebelBinding_Custom.bindinginfo.xml.  
  
-   Le fichier contient des informations sur la configuration de liaison, le type de liaison, l’URI de point de terminaison et l’action de port basé sur les opérations pour lesquelles les métadonnées a été générée. Lorsque vous importez ce fichier de liaison pour créer un port, toutes les informations requises pour configurer un port physique sont définies automatiquement sur le port.  
  
    > [!IMPORTANT]
    >  Par défaut, l’action sur le port d’envoi est mappée au nom d’opération pour lequel générer des métadonnées. Par exemple, si vous générez des métadonnées pour l’opération d’insertion sur le composant de gestion de compte, l’action sur le port est définie sur `<Operation Name="Insert" Action="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert " />`. Toutefois, le nom de l’opération sur le port d’envoi logique que vous créez dans le Concepteur d’orchestration BizTalk n’a pas peut être le même. Vous devez vous assurer que le nom de l’opération dans le port logique (dans l’orchestration BizTalk) et le port d’envoi physique (dans la console Administration de BizTalk Server) sont les mêmes. Si ce n’est pas le cas, vous recevez une erreur lors de l’envoi des messages au système Siebel via le port d’envoi.  
  
-   Vous devez uniquement fournir les informations d’identification pour le port pour se connecter au système Siebel. Alors que le fichier de liaison ne conserve pas le nom d’utilisateur avec lequel se connecter, pour des raisons de sécurité le fichier de liaison ne contient pas le mot de passe.  
  
## <a name="key-considerations-for-using-the-port-binding-file"></a>Considérations relatives à la clé pour l’utilisation du fichier de liaison de Port  
  
-   Lorsque vous importez le fichier de liaison, vous pouvez obtenir un message de la boîte de dialogue informant que le nom d’application BizTalk dans le fichier de liaison ne correspond pas au nom de l’application à laquelle vous importez le fichier de liaison. Vous pouvez ignorer ce message et continuer.  
  
-   Également, le fichier de liaison contient les noms des ports et emplacements de réception. Si l’application BizTalk à laquelle vous importez le fichier de liaison crée un port ou un emplacement de réception qui porte le même nom qu’un port déjà existant dans la même application BizTalk, vous obtiendrez une erreur. Vous devez modifier manuellement le fichier de liaisons pour spécifier un nom unique pour les ports ou les emplacements de réception.  
  
-   Par défaut, le fichier de liaison de port contient toujours des définitions pour les ports d’envoi bidirectionnels. Lorsque vous importez ce fichier dans une application BizTalk, il crée un port d’envoi bidirectionnel. Toutefois, vous pouvez avoir une orchestration qui a un port d’envoi unidirectionnel. Par conséquent, lorsque vous configurez telle une orchestration et que vous utilisez le port créé par l’importation du fichier de liaison, le port n’est pas disponible dans la liste. Cela se produit, car le port logique que vous avez créé dans le cadre de l’orchestration est un port unidirectionnel alors que le port physique créé dans l’orchestration est un port bidirectionnel. Dans ce cas, vous pouvez modifier le fichier de liaisons pour apporter les modifications suivantes :  
  
    |Pour cela|Action|  
    |--------------|-------------|  
    |Pour modifier le fichier de liaisons de port pour configurer un port d’envoi unidirectionnel|-Dans l’extrait suivant, remplacez la valeur de **IsTwoWay** propriété **false**. À l’origine, il est défini sur **true**.<br /><br /> `<SendPort Name="port_name" IsStatic="true" IsTwoWay="false" BindingOption="0">`<br /><br /> -Mettez en commentaire les extraits suivants :<br /><br /> `<ReceivePipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLReceive"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLReceive,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="1" TrackingOption="None" Description=""/>`<br /><br /> `<ReceivePipelineData xsi:nil="true" />`|  
  
## <a name="configuring-a-wcf-siebel-port-using-the-port-binding-file-generated-using-consume-adapter-service-add-in"></a>Configuration d’un Port WCF-Siebel à l’aide du fichier de liaison de Port généré à l’aide de Consume Adapter Service Add-in  
 Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée également un fichier de liaison de port que vous pouvez importer dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous pouvez utiliser le même fichier de liaison de port permettent pour également de créer le port BizTalk WCF-Siebel dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Toutefois, avant de créer le port de WCF-Siebel, vous devez effectuer les tâches suivantes pour modifier le fichier de liaison de port.  
  
1.  Ouvrez le fichier de liaison de port dans un éditeur de texte.  
  
2.  Recherchez et remplacez « WCF-Custom » avec le nom avec lequel vous avez ajouté l’adaptateur WCF-Siebel dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Par exemple, si vous avez ajouté l’adaptateur WCF-Siebel en tant que « SiebelAdapter », remplacez « WCF-Custom » avec « SiebelAdapter ».  
  
3.  Recherchez l’attribut « ConfigurationClsid » et remplacez la valeur existante de l’attribut « 7971A78D-AE8F-42B4-834D-3A957FD945E9 ».  
  
4.  Enregistrez et fermez le fichier de liaison.  
  
5.  Importer le fichier de liaison dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Consultez [réutiliser les liaisons de l’adaptateur dans l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md). 
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications BizTalk avec le Siebel 

carte] (.. /.. / adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)