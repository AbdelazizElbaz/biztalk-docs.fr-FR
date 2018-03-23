---
title: À l’aide de l’outil Service Model Metadata Tool avec l’adaptateur BizTalk pour base de données Oracle dans BizTalk Server | Documents Microsoft
description: Utiliser svcutil.exe pour une liaison non définis par défaut, ou pour créer une classe de Client WCF ou le contrat de Service WCF avec l’adaptateur de base de données Oracle - Pack de l’adaptateur BizTalk (LOB)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8660014-da04-4692-89e8-f14fcb419496
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dfbdbd60333a2e5683b4f37a65edb928a451e46
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="using-the-servicemodel-metadata-utility-tool-with-the-biztalk-adapter-for-oracle-database"></a>À l’aide de l’outil Service Model Metadata Tool avec l’adaptateur BizTalk pour base de données Oracle
Vous pouvez utiliser le service Model Metadata Utility Tool (svcutil.exe) pour générer une classe de client WCF ou un contrat de service WCF (interface) pour les opérations qui les [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] expose. Après avoir exécuté svcutil.exe pour générer une classe de client WCF ou d’un contrat de service WCF, vous pouvez inclure le fichier généré dans votre code et créer des instances de la classe générée ou implémenter un service WCF dans le contrat pour effectuer des opérations sur Oracle base de données.  
  
 À l’aide de svcutil.exe vous oblige à fournir une URI qui contient les informations d’identification de connexion. Étant donné que, par défaut, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] désactive les informations d’identification dans l’URI de connexion, vous devez configurer svcutil.exe pour utiliser une liaison non définis par défaut pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 Les sections suivantes vous montrent comment configurer svcutil.exe et comment utiliser svcutil.exe pour générer le code du client WCF ou un contrat de service WCF avec les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
##  <a name="BKMK_ConfigureSvcutil"></a> Configuration de svcutil.exe pour une liaison non définis par défaut   
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
          <endpoint name="oracledb"  
                    binding="oracleDBBinding"  
                    bindingConfiguration="OracleDBBinding"  
                    contract="IMetadataExchange" />  
        </client>  
        <bindings>  
            <oracleDBBinding>  
                <binding name="OracleDBBinding" acceptCredentialsInUri="true" />  
            </oracleDBBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
> [!NOTE]
>  Vous pouvez définir les propriétés de liaison de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] dans la configuration de liaison.  
  
 Pour plus d’informations sur la configuration d’une liaison par défaut de svcutil.exe, consultez la rubrique « Custom sécuriser les métadonnées Endpoint » dans la documentation WCF à [ http://go.microsoft.com/fwlink/?LinkId=96077 ](http://go.microsoft.com/fwlink/?LinkId=96077).  
  
### <a name="configure-a-non-default-binding-for-the-pollingstmt-operation"></a>Configurer un Non-liaison par défaut pour l’opération POLLINGSTMT  
 Pour créer un contrat de service WCF pour l’opération POLLINGSTMT à l’aide de svcutil.exe, vous devez configurer la liaison par défaut pour inclure les **pollingStatement** propriété, en plus de **acceptCredentialsInUri**. Le **pollingStatement** doit contenir l’instruction SELECT qui cible la table. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise cette propriété pour générer la classe qui représente le résultat fortement typée la valeur que l’opération POLLINGSTMT retourne. L’exemple suivant montre une configuration de liaison qui est utilisée pour générer un contrat de service WCF pour une opération POLLINGSTMT qui cible la table /SCOTT/EMP.  
  
```  
<bindings>  
    <oracleDBBinding>  
        <binding name="OracleDBBinding" acceptCredentialsInUri="true"   
                                   pollingStatement="SELECT * FROM EMP FOR UPDATE" />  
    </oracleDBBinding>  
</bindings>  
```  
  
## <a name="create-a-wcf-client-class-or-wcf-service-contract-with-svcutilexe"></a>Créez une classe de Client WCF ou d’un contrat de Service WCF avec svcutil.exe  
 Pour utiliser svcutil.exe pour générer le code du client WCF ou un contrat de service WCF (interface) pour le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez fournir une URI qui spécifie un point de terminaison WS-MEX (Metadata Exchange) et l’ou les opérations dont vous voulez svcutil.exe pour connexion générer du code. Vous devez également spécifier des informations d’identification de connexion pour la base de données Oracle dans l’URI de connexion.  
  
> [!NOTE]
>  Avant de pouvoir utiliser svcutil.exe avec la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez le configurer pour utiliser un non définis par défaut de liaison ; pour plus d’informations sur la procédure à suivre, consultez [configuration de svcutil.exe pour l’adaptateur de base de données Oracle](#BKMK_ConfigureSvcutil).  
  
 Vous spécifiez une opération de point de terminaison et la cible MEX dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] URI de connexion de la manière suivante :  
  
-   Vous devez inclure le paramètre « wsdl » dans query_string. S’il est le premier paramètre de query_string, elle est spécifiée juste après le point d’interrogation ( ?). Si elle n’est pas le premier paramètre, il doit être précédée d’une esperluette (&).  
  
-   Vous devez suivre le paramètre « wsdl » par un ou plusieurs paramètres de « op ». Chaque paramètre de « op » est précédé par une esperluette (&) et spécifie l’ID de nœud d’une opération de cible.  
  
 Les trois exemples suivants montrent comment cibler différentes opérations à l’aide de svcutil.exe.  
  
 Cet exemple crée une classe de client WCF pour une opération d’insertion sur la table /SCOTT/EMP.  
  
 **.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"**  
  
 Cet exemple crée une classe de client WCF pour l’insertion et les opérations de suppression sur la table /SCOTT/EMP.  
  
 **.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"**  
  
 Cet exemple crée un contrat de service WCF pour l’opération POLLLINGSTMT. (Pour utiliser svcutil.exe pour générer un contrat de service WCF pour l’opération POLLINGSTMT, vous devez configurer une liaison par défaut de svcutil.exe, qui inclut une instruction d’interrogation).  
  
 **.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT"**  
  
> [!IMPORTANT]
>  Vous devez placer l’URI de connexion dans des guillemets sur la ligne de commande. Sinon, svcutil.exe essaie de récupérer les métadonnées pour les opérations qui les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge. Les résultats d’une tentative de ce type ne sont pas définis.  
  
 Par défaut, svcutil.exe place le code généré dans le fichier output.cs ; Toutefois, vous pouvez modifier le nom du fichier de sortie et de nombreuses autres options svcutil.exe utilise en définissant des commutateurs de ligne de commande. Pour plus d’informations sur les options que svcutil.exe prend en charge, consultez la rubrique « Utilitaire les Metadata de ServiceModel-Tool (Svcutil.exe) » dans la documentation WCF à [ http://go.microsoft.com/fwlink/?LinkId=72777 ](http://go.microsoft.com/fwlink/?LinkId=72777).  
  
 SvcUtil.exe ne fournit pas la fonction de recherche pour les opérations (par exemple, en utilisant des caractères génériques). Vous devez spécifier explicitement les ID de nœud pour les opérations spécifiques que vous souhaitez cibler. Vous ne pouvez pas spécifier les ID font référence uniquement aux catégories de nœud. Pour plus d’informations sur l’ID du nœud qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces, consultez [ID de nœud de métadonnées](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).  
  
 Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] offre des avancées et fonctionnalités de recherche qui peuvent grandement simplifier la génération d’une classe de client WCF et d’un contrat de service WCF. Pour plus d’informations sur la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], consultez [génération d’un Client WCF ou un contrat de Service WCF pour les artefacts de Solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et schémas de message pour l’adaptateur BizTalk pour Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)