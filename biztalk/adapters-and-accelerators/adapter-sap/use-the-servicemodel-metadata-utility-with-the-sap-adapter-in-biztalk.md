---
title: À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour mySAP Business Suite | Documents Microsoft
description: Utiliser svcutil.exe pour une liaison non définis par défaut, ou pour créer une classe de Client WCF ou le contrat de Service WCF avec l’adaptateur SAP - Pack de l’adaptateur BizTalk (LOB)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ServiceModel Metadata Utility Tool, creating a WCF Client Class or a WCF service contract with the tool
- ServiceModel Metadata Utility Tool, configuring the tool for the adapter
ms.assetid: 7ac08012-bb12-4983-9402-be84fe3997d8
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15c4612db6e3cde4e46385b1c5d1810fbb00eb70
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-mysap-business-suite"></a>À l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour mySAP Business Suite
Vous pouvez utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ou un contrat de service WCF (interface) pour les opérations qui les [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] expose. Après avoir exécuté svcutil.exe pour générer une classe de client WCF ou d’un contrat de service WCF, vous pouvez inclure le fichier généré dans votre code et créer des instances de la classe générée ou implémenter un service WCF à partir de l’interface générée pour effectuer des opérations sur SAP système.  
  
 À l’aide de svcutil.exe vous oblige à fournir une URI qui contient les informations d’identification de connexion. Étant donné que, par défaut, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] désactive les informations d’identification dans l’URI de connexion, vous devez configurer svcutil.exe pour utiliser une liaison non définis par défaut pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Vous pouvez également configurer les autres propriétés de liaison dans la liaison par défaut ; par exemple, pour créer un client WCF pour des opérations BAPI, vous devez définir le **EnableSafeTyping** liaison de propriété **true**.  
  
 Les sections suivantes vous montrent comment configurer svcutil.exe et comment utiliser svcutil.exe pour générer le code du client WCF ou un contrat de service WCF avec les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
##  <a name="BKMK_ConfigureSvcutil"></a> Configuration de svcutil.exe pour l’adaptateur SAP  
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
          <!-- the name should match the required scheme of the WS-Metadata Exchange endpoint   
          and the contract should be "IMetadataExchange" -->  
          <endpoint name="sap"  
                    binding="sapBinding"  
                    bindingConfiguration="SAPBinding"  
                    contract="IMetadataExchange" />  
        </client>  
        <bindings>  
          <sapBinding>  
            <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
          </sapBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
 Vous pouvez définir les propriétés de liaison de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans la configuration de liaison. Par exemple, vous pouvez spécifier la liaison par défaut suivante pour utiliser svcutil.exe pour générer un client WCF pour des opérations BAPI.  
  
```  
<bindings>  
  <sapBinding>  
    <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
  </sapBinding>  
</bindings>  
```  
  
 Pour plus d’informations sur la configuration d’une liaison par défaut de svcutil.exe, consultez le [personnalisé sécuriser les métadonnées de point de terminaison](https://msdn.microsoft.com/library/aa395212.aspx).
  
## <a name="creating-a-wcf-client-class-or-a-wcf-service-contract-with-svcutilexe"></a>Création d’une classe de Client WCF ou d’un contrat de Service WCF avec svcutil.exe  
 Pour utiliser svcutil.exe pour générer le code du client WCF ou un contrat de service WCF (interface) pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez fournir une URI qui spécifie un point de terminaison WS-MEX (Metadata Exchange) et l’ou les opérations dont vous voulez svcutil.exe pour connexion générer du code. Vous devez également spécifier des informations d’identification de connexion pour le système SAP dans l’URI de connexion.  
  
> [!NOTE]
>  Avant de pouvoir utiliser svcutil.exe avec la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez le configurer pour utiliser un non définis par défaut de liaison ; pour plus d’informations sur la procédure à suivre, consultez [configuration de svcutil.exe pour l’adaptateur SAP](#BKMK_ConfigureSvcutil).  
  
 Vous spécifiez une opération de point de terminaison et la cible MEX dans le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] URI de connexion de la manière suivante :  
  
-   Vous devez inclure le paramètre « wsdl » dans la chaîne de requête. S’il est le premier paramètre dans la chaîne de requête, il est spécifié juste après le point d’interrogation ( ?). Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).  
  
-   Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ». Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’ID de nœud d’une opération de cible.  
  
 Les trois exemples suivants montrent comment cibler différentes opérations à l’aide de svcutil.exe.  
  
 Cet exemple crée une classe de client WCF pour RFC_CALCULATE_TAXES.  
  
 **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CALCULATE_TAXES"**  
  
 Cet exemple crée une classe de client WCF pour les SALESORDER_CREATEFROMDAT201 et SALESORDER_CREATEFROMDAT202 IDOC.  
  
 **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"**  
  
 Cet exemple crée un contrat de service WCF pour recevoir l’IDOC SALESORDER_CREATEFROMDAT201 à partir du système SAP. L’ID de nœud spécifie une opération de réception. Cet exemple porte sur la récupération des métadonnées, il n’est pas nécessaire de spécifier les paramètres de l’écouteur dans query_string de l’URI de connexion.  
  
 **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Receive"**  
  
> [!IMPORTANT]
>  Vous devez placer l’URI de connexion dans des guillemets sur la ligne de commande. Sinon, svcutil.exe essaie de récupérer les métadonnées pour les opérations qui les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge. Les résultats d’une tentative de ce type ne sont pas définis.  
  
 Par défaut, svcutil.exe place le code généré dans le fichier output.cs ; Toutefois, vous pouvez modifier le nom du fichier de sortie et de nombreuses autres options svcutil.exe utilise en définissant des commutateurs de ligne de commande. Pour plus d’informations sur les options que svcutil.exe prend en charge, consultez la [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
 SvcUtil.exe ne fournit pas la fonction de recherche pour les opérations (par exemple, en utilisant des caractères génériques). Vous devez spécifier explicitement les ID de nœud pour les opérations spécifiques que vous souhaitez cibler. L’ID de nœud d’une opération est équivalente à la chaîne d’action de message. Vous ne pouvez pas spécifier les ID font référence uniquement aux catégories de nœud. Pour plus d’informations sur l’ID du nœud qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
 Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] offre des avancées et fonctionnalités de recherche qui peuvent grandement simplifier la génération d’une classe de client WCF et d’un contrat de service WCF. Pour plus d’informations sur la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
