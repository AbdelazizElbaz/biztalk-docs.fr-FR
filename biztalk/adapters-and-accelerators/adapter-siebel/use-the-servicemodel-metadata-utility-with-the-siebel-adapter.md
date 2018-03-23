---
title: À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft
description: Utiliser svcutil.exe pour une liaison non définis par défaut, ou pour créer une classe de Client WCF ou le contrat de Service WCF avec l’adaptateur Siebel - Pack de l’adaptateur BizTalk (LOB)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03d16481-cc8b-4e28-a33c-92e48a9a7e8f
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0bcf80d4a1ea9fc6b54403faa14084816e413be
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-siebel-ebusiness-applications"></a>À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour Siebel eBusiness Applications
Vous pouvez utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF pour les opérations qui les [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] expose. Après avoir exécuté svcutil.exe pour générer une classe de client WCF, vous pouvez inclure le fichier généré dans votre code et créer des instances de la classe de client WCF pour effectuer des opérations sur le système Siebel.  
  
 À l’aide de svcutil.exe vous oblige à fournir une URI qui contient les informations d’identification de connexion. Étant donné que, par défaut, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] désactive les informations d’identification dans l’URI de connexion, vous devez configurer svcutil.exe pour utiliser une liaison non définis par défaut pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Vous pouvez également configurer les autres propriétés de liaison dans la liaison par défaut.  
  
 Les sections suivantes vous montrent comment configurer svcutil.exe et comment utiliser svcutil.exe pour générer le code du client WCF avec les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
##  <a name="BKMK_ConfigureSvcutil"></a>Configuration de svcutil.exe pour une liaison non définis par défaut   
 Pour configurer svcutil.exe pour utiliser une liaison non définis par défaut, vous devez créer une copie locale de svcutil.exe et ensuite créer ou modifier une copie locale du fichier de configuration svcutil.exe.config.  
  
 
1.  Créez un dossier et copier svcutil.exe dans le nouveau dossier. Vous pouvez généralement trouver svcutil.exe à l’emplacement d’installation du SDK Windows, en particulier, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
2.  Créez un fichier appelé svcutil.exe.config dans le nouveau dossier.  
  
3.  Ajouter une liaison et un point de terminaison client dans le fichier svcutil.exe.config. Vous devez exécuter svcutil.exe depuis le nouveau dossier pour vous assurer que la configuration correcte est utilisée.  
  
    > [!IMPORTANT]
    >  L’attribut de nom du point de terminaison client doit spécifier le schéma utilisé dans l’URI de connexion. Cette valeur respecte la casse.  
  
    ```  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <!-- the name should match the required scheme of the Metadata Exchange endpoint   
          and the contract should be "IMetadataExchange" -->  
          <endpoint name="siebel"  
            binding="siebelBinding"  
            bindingConfiguration="SiebelBinding"  
            contract="IMetadataExchange" />  
        </client>  
        <bindings>  
          <siebelBinding>  
            <binding name="SiebelBinding" acceptCredentialsInUri="true" />  
          </siebelBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
  
    ```  
  
> [!NOTE]
>  Vous pouvez définir les propriétés de liaison de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans la configuration de liaison.  
  
 Pour plus d’informations sur la configuration d’une liaison par défaut de svcutil.exe, consultez la rubrique « Custom sécuriser les métadonnées Endpoint » dans la documentation WCF à [ http://go.microsoft.com/fwlink/?LinkId=96077 ](http://go.microsoft.com/fwlink/?LinkId=96077).  
  
## <a name="creating-a-wcf-client-class-with-svcutilexe"></a>Création d’une classe de Client WCF avec svcutil.exe  
 Pour utiliser svcutil.exe pour générer le code du client WCF pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], vous devez fournir une connexion URI qui spécifie un **IMetadataExchange** (mex) au point de terminaison et l’ou les opérations pour lequel vous voulez svcutil.exe pour générer code. Vous devez également spécifier des informations d’identification de connexion pour le système Siebel dans l’URI de connexion.  
  
> [!NOTE]
>  Avant de pouvoir utiliser svcutil.exe avec la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], vous devez le configurer pour utiliser un non définis par défaut de liaison ; pour plus d’informations sur la procédure à suivre, consultez [configuration de svcutil.exe pour l’adaptateur Siebel](#BKMK_ConfigureSvcutil).  
  
 Vous spécifiez une opération de point de terminaison et la cible mex dans le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] URI de connexion de la manière suivante :  
  
-   Vous devez inclure le paramètre « wsdl » dans query_string. S’il est le premier paramètre de query_string, elle est spécifiée juste après le point d’interrogation ( ?). Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).  
  
-   Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ». Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’ID de nœud d’une opération de cible.  
  
 Les deux exemples suivants montrent comment cibler différentes opérations à l’aide de svcutil.exe.  
  
 Cet exemple crée une classe de client WCF pour une opération d’insertion dans l’objet métier ACCOUNT\ACCOUNT.  
  
 **.\svcutil "siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert"**  
  
 Cet exemple crée une classe de client WCF pour une opération d’insertion et une opération de suppression sur l’objet métier ACCOUNT\ACCOUNT.  
  
 **.\svcutil " siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelEnterpriseServer=ent_server&SiebelObjectManager=obj_mgr&Language=enu&wsdl&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert&op=http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Delete"**  
  
> [!IMPORTANT]
>  Vous devez placer l’URI de connexion dans des guillemets sur la ligne de commande. Sinon, svcutil.exe essaie de récupérer les métadonnées pour les opérations qui les [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne prend pas en charge. Les résultats d’une tentative de ce type ne sont pas définis.  
  
 Par défaut, svcutil.exe place le code généré dans le fichier output.cs ; Toutefois, vous pouvez modifier le nom du fichier de sortie et de nombreuses autres options svcutil.exe utilise en définissant des commutateurs de ligne de commande.  
  
 SvcUtil.exe ne fournit pas la fonction de recherche pour les opérations (par exemple, en utilisant des caractères génériques). Vous devez spécifier explicitement les ID de nœud pour les opérations spécifiques que vous souhaitez cibler. Vous ne pouvez pas spécifier les ID font référence uniquement aux catégories de nœud. Pour plus d’informations sur l’ID du nœud qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-siebel/metadata-node-ids1.md).  
  
 Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] fournit les fonctionnalités de recherche qui peuvent grandement simplifier la génération d’une classe de client WCF et les parcourir avancée. Pour plus d’informations sur la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Siebel](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md).  
  
