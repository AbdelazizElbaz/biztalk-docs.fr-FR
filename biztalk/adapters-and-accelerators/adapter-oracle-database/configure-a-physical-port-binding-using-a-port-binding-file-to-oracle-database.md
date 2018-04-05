---
title: Configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- physical port binding, configuring by using a port binding file
ms.assetid: 154d219e-c6f3-4f70-9ac5-d9345f5260e9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 716688ab3cbc2431c6058fee17f9dae42ca96ded
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database"></a>Configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle
Lorsque vous utilisez la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées pour un artefact de base de données Oracle, autres que les fichiers de schéma, le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère également un fichier de liaison de port. Vous pouvez importer ce fichier de liaison dans votre application BizTalk pour créer un envoi physique ou de port de réception. Pour obtenir des instructions sur l’importation de fichiers de liaison, consultez [liaisons de l’adaptateur de base de données Oracle de réutiliser](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md). Si vous importez ce fichier de liaison, vous n’avez pas à créer un envoi physique manuellement ou de port de réception.  
  
> [!IMPORTANT]
>  Lors de l’utilisation du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier de liaison. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier de liaison, si nécessaire.  
  
 Création d’un port à l’aide d’un fichier de liaison de port toujours crée un envoi bidirectionnel ou des ports de réception. Si vous souhaitez créer d’envoi unidirectionnel ou de ports de réception, vous pouvez le créer manuellement en suivant la procédure mentionnée dans [configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md). Ou bien, vous pouvez suivre les solutions de contournement décrites dans cette rubrique pour modifier le fichier de liaison de port pour créer d’envoi unidirectionnel ou de ports de réception.  
  
 Voici quelques points clés que vous devez comprendre en ce qui concerne le fichier de liaison généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]:  
  
-   Les fichiers sont créés avec une convention d’affectation de noms spécifique. Si vous avez généré des métadonnées pour les opérations sortantes, qui consiste à envoyer des messages à la base de données Oracle, le nom du fichier est WcfSendPort_OracleDBBinding_Custom.bindinginfo.xml.  
  
     Si vous avez généré des métadonnées pour les opérations entrantes, qui doit recevoir des messages à partir de la base de données Oracle, le nom du fichier est WcfReceivePort_OracleDBBinding_Custom.bindinginfo.xml.  
  
-   Le fichier contient des informations sur la configuration de liaison, le type de liaison, l’URI de point de terminaison et l’action de port basé sur les opérations pour lesquelles les métadonnées a été générée. Lorsque vous importez ce fichier de liaison pour créer un port, toutes les informations requises pour configurer un port physique sont définies automatiquement sur le port.  
  
    > [!IMPORTANT]
    >  Par défaut, l’action sur le port d’envoi est mappée au nom d’opération pour lequel générer des métadonnées. Par exemple, si vous générez des métadonnées pour une opération Select sur la table ACCOUNTACTIVITY, l’action sur le port est définie sur `<Operation Name="Select" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select" />`. Toutefois, le nom de l’opération sur le port d’envoi logique que vous créez dans le Concepteur d’orchestration BizTalk n’a pas peut être le même. Vous devez vous assurer que le nom de l’opération dans le port logique (dans l’orchestration BizTalk) et le port d’envoi physique (dans la console Administration de BizTalk Server) sont les mêmes. Si ce n’est pas le cas, vous recevez une erreur lors de l’envoi de messages à la base de données Oracle par le biais du port d’envoi.  
  
-   Vous devez uniquement fournir les informations d’identification pour le port pour se connecter à la base de données Oracle. Alors que le fichier de liaison ne conserve pas le nom d’utilisateur avec lequel se connecter, pour des raisons de sécurité le fichier de liaison ne contient pas le mot de passe.  
  
## <a name="key-considerations-for-using-the-port-binding-file"></a>Considérations relatives à la clé pour l’utilisation du fichier de liaison de Port  
  
-   Lorsque vous importez le fichier de liaison, vous pouvez obtenir un message de la boîte de dialogue informant que le nom d’application BizTalk dans le fichier de liaison ne correspond pas au nom de l’application à laquelle vous importez le fichier de liaison. Vous pouvez ignorer ce message et continuer.  
  
-   Également, le fichier de liaison contient les noms des ports et emplacements de réception. Si l’application BizTalk à laquelle vous importez le fichier de liaison crée un port ou un emplacement de réception qui porte le même nom qu’un port déjà existant dans la même application BizTalk, vous obtiendrez une erreur. Vous devez modifier manuellement le fichier de liaisons pour spécifier un nom unique pour les ports ou les emplacements de réception.  
  
-   Le fichier de liaison contient également des informations sur l’URI de connexion. Si le fichier de liaison crée un emplacement de réception qui a le même URI de réception comme emplacement de réception existant déjà dans la même application BizTalk, vous obtiendrez une erreur. Vous devez modifier manuellement le fichier de liaison pour spécifier un URI unique. Vous pouvez spécifier un URI unique en incluant un ID d’interrogation.  
  
-   Par défaut, le fichier de liaison de port contient toujours les définitions pour les ports bidirectionnels (envoi ou réception). Lorsque vous importez ce fichier dans une application BizTalk, il crée un envoi bidirectionnel ou port de réception. Toutefois, vous disposez d’une orchestration qui a un envoi monodirectionnel ou port de réception. Par conséquent, lorsque vous configurez telle une orchestration et que vous utilisez le port créé par l’importation du fichier de liaison, le port n’est pas disponible dans la liste. Cela se produit, car le port logique que vous avez créé dans le cadre de l’orchestration est un port unidirectionnel alors que le port physique créé dans l’orchestration est un port bidirectionnel. Dans ce cas, vous pouvez modifier le fichier de liaisons pour apporter les modifications suivantes :  
  
    |Pour cela|Action|  
    |--------------|-------------|  
    |Pour modifier le fichier de liaisons de port pour configurer un port d’envoi unidirectionnel|-Dans l’extrait suivant, remplacez la valeur de **IsTwoWay** propriété sur false. À l’origine, ce paramètre est défini sur true.<br /><br /> `<SendPort Name="port_name" IsStatic="true" IsTwoWay="false" BindingOption="0">`<br /><br /> -Mettez en commentaire les extraits suivants :<br /><br /> `<ReceivePipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLReceive"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLReceive,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="1" TrackingOption="None" Description=""/>`<br /><br /> `<ReceivePipelineData xsi:nil="true" />`|  
    |Pour modifier le fichier de liaisons de port pour configurer un port de réception unidirectionnel|-Dans l’extrait suivant, remplacez la valeur de **IsTwoWay** propriété sur false. À l’origine, ce paramètre est défini sur true.<br /><br /> `<ReceivePort Name="port_name" IsTwoWay="false" BindingOption="1">`<br /><br /> -Mettez en commentaire les extraits suivants :<br /><br /> `<SendPipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLTransmit"    FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLTransmit,    Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,    PublicKeyToken=token" Type="2" TrackingOption="None" Description="" />`<br /><br /> `<SendPipelineData xsi:nil="true" />`<br /><br /> `<SendPipelineData xsi:nil="true" />`|  
  
## <a name="configuring-a-wcf-oracledb-port-using-the-port-binding-file-generated-using-consume-adapter-service-add-in"></a>Configuration d’un Port WCF-OracleDB à l’aide du fichier de liaison de Port généré à l’aide de Consume Adapter Service Add-in  
 Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée un fichier de liaison de port que vous pouvez importer dans la console Administration de BizTalk Server. Vous pouvez utiliser le même fichier de liaison de port permettent pour également de créer le port BizTalk WCF-OracleDB dans la console Administration de BizTalk Server. Toutefois, avant de créer le port de WCF-OracleDB, vous devez effectuer les tâches suivantes pour modifier le fichier de liaison de port.  
  
1.  Ouvrez le fichier de liaison de port dans un éditeur de texte.  
  
2.  Recherchez et remplacez « WCF-Custom » avec le nom avec lequel vous avez ajouté l’adaptateur WCF-OracleDB dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Par exemple, si vous avez ajouté l’adaptateur WCF-OracleDB en tant que « OracleDBAdapter », remplacez « WCF-Custom » avec « OracleDBAdapter ».  
  
3.  Recherchez l’attribut « ConfigurationClsid » et remplacez la valeur existante de l’attribut « D7127586-E851-412e-8A8A-2428AEDDC219 ».  
  
4.  Enregistrez et fermez le fichier de liaison.  
  
5.  Importer le fichier de liaison dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions sur la façon d’importer le fichier de liaison, consultez [liaisons de l’adaptateur de base de données Oracle de réutiliser](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)