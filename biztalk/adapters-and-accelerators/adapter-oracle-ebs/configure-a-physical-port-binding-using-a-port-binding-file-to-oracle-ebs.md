---
title: "Configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c3c468e-815c-4611-879c-8da9111eeb3b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a6f582733b6ff545e96c671d7c98f58c211e6ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-e-business-suite"></a>Configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Oracle E-Business Suite
Lorsque vous utilisez la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer des métadonnées pour les artefacts d’Oracle E-Business Suite, autres que les fichiers de schéma, le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère également un fichier de liaison de port. Vous pouvez importer ce fichier de liaison dans votre application BizTalk pour créer un envoi physique ou de port de réception. Pour obtenir des instructions sur l’importation de fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md). Si vous importez ce fichier de liaison, vous n’avez pas à créer un envoi physique manuellement ou de port de réception.  
  
> [!IMPORTANT]
>  Lors de l’utilisation du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], si vous ne spécifiez pas une valeur pour une propriété de liaison de type chaîne et dont la valeur par défaut a la valeur null puis que la liaison de propriété sera pas disponible dans le fichier de liaison. Vous devez ajouter manuellement la propriété de liaison et sa valeur dans le fichier de liaison, si nécessaire.  
  
 Création d’un port à l’aide du fichier de liaison de port de toujours crée un port d’envoi bidirectionnel ou port de réception unidirectionnel. Si vous souhaitez créer un port d’envoi unidirectionnel, vous pouvez le créer manuellement en suivant la procédure mentionnée dans [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md). Ou bien, vous pouvez suivre les solutions de contournement décrites dans cette rubrique pour modifier le fichier de liaison de port pour créer des ports d’envoi unidirectionnels.  
  
> [!NOTE]
>  Pour les opérations entrantes, le fichier de liaison de port seront toujours créer un port de réception unidirectionnel. C’est parce que le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] seul port pour les opérations entrantes de réception unidirectionnel de la prise en charge.  
  
> [!IMPORTANT]
>  À l’aide de la [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] ne crée pas un fichier de liaison de port à l’aide de laquelle vous pouvez créer un port WCF-OracleEBS. Toutefois, vous pouvez apporter des modifications dans le fichier de liaison de port généré par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] et l’utiliser pour créer un port WCF-OracleEBS. Pour plus d’informations, consultez [configuration d’un Port WCF-OracleEBS avec le complément, Port de liaison fichier généré à l’aide de Consume Adapter Service](#BKMK_ModifyBinding).  
  
 Voici quelques points clés que vous devez comprendre en ce qui concerne la liaison de fichiers qui le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] génère :  
  
-   Les fichiers sont créés avec une convention d’affectation de noms spécifique. Si vous avez généré des métadonnées pour les opérations sortantes, autrement dit, pour envoyer des messages pour Oracle E-Business Suite, le nom du fichier est WcfSendPort_OracleEBSBinding_Custom.bindinginfo.xml.  
  
     Si vous avez généré des métadonnées pour les opérations entrantes, autrement dit, pour recevoir des messages à partir d’Oracle E-Business Suite, le nom du fichier est WcfReceivePort_OracleEBSBinding_Custom.bindinginfo.xml.  
  
-   Le fichier contient des informations sur la configuration de liaison, le type de liaison, l’URI de point de terminaison et l’action de port basé sur les opérations pour lesquelles les métadonnées a été générée. Lorsque vous importez ce fichier de liaison dans votre application BizTalk pour créer un port, toutes les informations requises pour configurer un port physique sont automatiquement définies sur le port.  
  
    > [!IMPORTANT]
    >  Par défaut, l’action sur le port d’envoi est mappée au nom d’opération pour laquelle vous avez généré des métadonnées. Par exemple, si vous générez des métadonnées pour l’opération d’insertion sur la table d’interface (par exemple, FA_BOOKS), l’action sur le port est définie sur `<Operation Name="Insert" Action="InterfaceTables/Insert/OFA/FA/FA_BOOKS" />`. Toutefois, le nom de l’opération sur le port d’envoi logique que vous créez dans le Concepteur d’orchestration BizTalk n’a pas peut être le même. Vous devez vous assurer que le nom de l’opération dans la logique d’envoi port (dans l’orchestration BizTalk) et le port d’envoi physique (dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration) sont identiques. Si ce n’est pas le cas, vous recevez une erreur lors de l’envoi de messages pour Oracle E-Business Suite via le port d’envoi.  
  
-   Vous devez uniquement fournir les informations d’identification pour le port pour se connecter à Oracle E-Business Suite. Bien que le fichier de liaison ne conserve pas le nom d’utilisateur avec lequel se connecter, pour des raisons de sécurité le fichier de liaison ne contient pas le mot de passe.  
  
## <a name="key-considerations-for-using-the-port-binding-file"></a>Considérations relatives à la clé pour l’utilisation du fichier de liaison de Port  
  
-   Lorsque vous importez le fichier de liaison, vous pouvez obtenir un message de la boîte de dialogue informant que le nom d’application BizTalk dans le fichier de liaison ne correspond pas au nom de l’application à laquelle vous importez le fichier de liaison. Vous pouvez ignorer ce message et continuer.  
  
-   Également, le fichier de liaison contient les noms des ports et emplacements de réception. Si l’application BizTalk à laquelle vous importez le fichier de liaison crée un port ou un emplacement de réception qui porte le même nom qu’un port déjà existant dans la même application BizTalk, vous obtiendrez une erreur. Vous devez modifier manuellement le fichier de liaison pour spécifier un nom unique pour les ports ou les emplacements de réception.  
  
-   Le fichier de liaison contient également des informations sur l’URI de connexion. Si le fichier de liaison crée un emplacement de réception qui a le même URI de réception comme emplacement de réception existant déjà dans la même application BizTalk, vous obtiendrez une erreur. Vous devez modifier manuellement le fichier de liaison pour spécifier un URI unique.  
  
-   Par défaut, le fichier de liaison de port pour les opérations sortantes contient toujours des définitions pour un port d’envoi bidirectionnel. Lorsque vous importez ce fichier dans une application BizTalk, il crée un port d’envoi bidirectionnel. Toutefois, vous pouvez avoir une orchestration qui a un port d’envoi unidirectionnel. Par conséquent, lorsque vous configurez telle une orchestration et que vous utilisez le port créé par l’importation du fichier de liaison, le port n’est pas disponible dans la liste. Cela se produit, car le port logique que vous avez créé dans le cadre de l’orchestration est un port unidirectionnel alors que le port physique créé dans l’orchestration est un port bidirectionnel. Dans ce cas, vous pouvez modifier le fichier de liaison pour apporter les modifications suivantes :  
  
    |Pour cela|Action|  
    |--------------|-------------|  
    |Pour modifier le fichier de liaison de port pour configurer un port d’envoi unidirectionnel|1.  Dans l’extrait suivant, remplacez la valeur de la **IsTwoWay** propriété **false**. À l’origine, il est défini sur **true**.<br />     `<SendPort Name="port_name" IsStatic="true" IsTwoWay="false " BindingOption="0">`<br />2.  Commentez les extraits suivants :<br />     `<ReceivePipeline Name="Microsoft.BizTalk.DefaultPipelines.XMLReceive"   FullyQualifiedName="Microsoft.BizTalk.DefaultPipelines.XMLReceive,   Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral,   PublicKeyToken= token" Type="1" TrackingOption="None" Description=""/>`<br />     `<ReceivePipelineData xsi:nil="true" />`|  
  
    > [!IMPORTANT]
    >  Pour les opérations entrantes, le fichier de liaison de port seront toujours créer un port de réception unidirectionnel. C’est parce que le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] seul port pour les opérations entrantes de réception unidirectionnel de la prise en charge.  
  
##  <a name="BKMK_ModifyBinding"></a>Configuration d’un Port WCF-OracleEBS à l’aide du fichier de liaison de Port généré à l’aide de Consume Adapter Service Add-in  
 Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée un fichier de liaison de port que vous pouvez importer dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous pouvez utiliser le même fichier de liaison de port permettent pour également de créer le port BizTalk WCF-OracleEBS [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Toutefois, avant de créer le port de WCF-OracleEBS, vous devez effectuer les tâches suivantes pour modifier le fichier de liaison de port.  
  
1.  Ouvrez le fichier de liaison de port dans un éditeur de texte.  
  
2.  Recherchez et remplacez « WCF-Custom » avec le nom avec lequel vous avez ajouté l’adaptateur WCF-OracleEBS dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Par exemple, si vous avez ajouté l’adaptateur WCF-OracleEBS en tant que « OracleEBSAdapter », remplacez « WCF-Custom » avec « OracleEBSAdapter ».  
  
3.  Recherchez l’attribut « ConfigurationClsid » et remplacez la valeur existante de l’attribut « F452BB15-7A0D-495d-9395-C630D3FD29CD ».  
  
4.  Enregistrez et fermez le fichier de liaison.  
  
5.  Importer le fichier de liaison dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour obtenir des instructions sur la façon d’importer le fichier de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)