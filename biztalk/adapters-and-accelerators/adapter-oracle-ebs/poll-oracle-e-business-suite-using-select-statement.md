---
title: "Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81d70b36-8b80-4ab9-b97c-ee861aafbbac
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83e5b40d8176b8e4ba448cadf1676013db8f2706
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="poll-oracle-e-business-suite-using-select-statement"></a>Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT
Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de modification de données périodiques à l’aide d’une instruction SELECT pour l’interrogation de façon permanente les tables d’interface, interface, des vues, des tables et des vues dans Oracle E-Business Suite. Vous pouvez spécifier une instruction SELECT comme une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour Oracle E-Business Suite. Vous pouvez également spécifier un bloc de code après interrogation PL/SQL que l’adaptateur s’exécute après l’exécution de l’instruction d’interrogation.  
  
 Pour activer l’interrogation, vous devez spécifier le que port de réception de certaines propriétés de liaison sur le WCF-Custom ou WCF-OracleEBS.  Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md). Pour plus d’informations sur la structure du message SOAP pour les opérations d’interrogation, consultez [des schémas de Message pour les opérations d’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md).  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a>Configuration d’une opération d’interrogation avec liaison des propriétés de l’adaptateur Oracle E-Business Suite  
 Le tableau suivant récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] messages de modification des propriétés de liaison que vous utilisez pour configurer l’adaptateur pour recevoir des données. Vous devez spécifier ces propriétés de liaison lors de la configuration du port de réception [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer **d’interrogation** ou **Notification** opération entrante. Valeur par défaut est **d’interrogation**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. Uniquement si un enregistrement n’est disponible, l’instruction SELECT que vous spécifiez pour le **PollingInput** liaison de la propriété sera exécutée.|  
|**PollingInterval**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 30 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur est en veille pendant le temps restant dans l’intervalle.|  
|**PollingInput**|Spécifie l’instruction d’interrogation. Pour interroger à l’aide d’une instruction SELECT, vous devez spécifier une instruction SELECT pour cette propriété de liaison. La valeur par défaut est null.<br /><br /> Vous devez spécifier une valeur pour **PollingInput** propriété pour activer l’interrogation de liaison. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.|  
|**PollingAction**|Spécifie l’action pour l’opération d’interrogation. Vous pouvez déterminer l’action de l’interrogation d’une opération spécifique à partir des métadonnées que vous générez pour l’opération en utilisant la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].|  
|**PostPollStatement**|Spécifie un bloc d’instructions qui est exécuté après l’instruction spécifiée par le **PollingInput** propriété de liaison est exécutée.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence l’instruction d’interrogation, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient pour exécuter l’instruction d’interrogation à l’intervalle d’interrogation spécifié. La valeur par défaut est False.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger la base de données Oracle, poursuivre la lecture.  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de données modifier des messages à l’aide des instructions SELECT, créez un projet BizTalk et générer le schéma pour le **interrogation** opération pour la table que vous voulez interroger. Dans cette rubrique, nous générer le schéma pour le **interrogation** opération pour le **MS_SAMPLE_EMPLOYEE** table d’interface dans le **bibliothèque d’objets Application** application. Cette table est créée lorsque vous exécutez le script create_apps_artifacts.sql fourni avec les exemples pour créer ces objets dans Oracle E-Business Suite.  
  
 Ensuite, nous allons utiliser le routage basé sur le contenu (CBR) dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour configurer une application avec un port de réception qui reçoit des messages d’interrogation de la **MS_SAMPLE_EMPLOYEE** table d’interface, puis de le router vers un port d’envoi. Dans ce cas, nous allons créer un filtre sur le port d’envoi qui vérifie l’emplacement de réception spécifié et le message est routé vers le port d’envoi.  
  
 Pour illustrer une opération d’interrogation, nous les opérations suivantes :  
  
-   Spécifiez une instruction SELECT pour le **PolledDataAvailableStatement** liaison de propriété pour déterminer où l’interface table interrogés (MS_SAMPLE_EMPLOYEE) comporte des données. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table d’interface MS_SAMPLE_EMPLOYEE a des enregistrements.  
  
-   Spécifiez une instruction SELECT pour le **PollingInput** propriété de liaison. Cette instruction récupère toutes les lignes dans la table d’interface MS_SAMPLE_EMPLOYEE. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  
  
    > [!NOTE]
    >  Pour plus d’informations sur la clause FOR UPDATE utilisée dans l’instruction SELECT, consultez [interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md).  
  
-   Spécifiez une instruction DELETE en tant que partie de la **PostPollStatement** propriété de liaison. Cette instruction supprime toutes les données à partir de la table d’interface MS_SAMPLE_EMPLOYEE. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     Une fois que cela se produit, la prochaine fois que l’instruction spécifiée pour **PollingInput** sera exécutée, elle ne permet pas d’extraire des données.  
  
-   Jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE, vous n’obtiendrez pas les messages d’interrogation. Par conséquent, vous devez remplir de nouveau la table d’interface MS_SAMPLE_EMPLOYEE avec nouveaux enregistrements. Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.  
  
## <a name="how-to-receive-data-change-messages-from-oracle-e-business-suite"></a>La réception des Messages de modification de données à partir d’Oracle E-Business Suite  
 Une opération sur l’utilisation de base de données Oracle [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches procédurales suivantes décrites dans [blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour configurer l’adaptateur pour Oracle E-Business Suite à l’aide d’une instruction SELECT, ces tâches sont :  
  
1.  Créez un projet BizTalk et la génération du schéma pour le **interrogation** opération pour la table d’interface que vous voulez interroger.  
  
2.  Générez et déployez le projet BizTalk.  
  
3.  Configurer l’application en créant les ports d’envoi et de réception BizTalk. Ajoutez également le filtre sur le port d’envoi afin qu’il vérifie l’emplacement de réception spécifié dans le port de réception et d’interrogation de message est routé vers le port d’envoi.  
  
    > [!IMPORTANT]
    >  Pour les scénarios d’interrogation entrant que vous devez toujours configurer un port de réception unidirectionnel. Bidirectionnel recevoir des ports ne sont pas pris en charge pour les opérations entrantes.  
  
4.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, PollingUsingSelectStatement, en fonction de cette rubrique est également fourni avec BizTalk Adapter Pack. Pour plus d’informations, consultez [exemples](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Vous devez générer le schéma pour le **interrogation** opération sur la table d’interface MS_SAMPLE_EMPLOYEE dans le **bibliothèque d’objets Application** application. Effectuer les tâches suivantes lors de la génération de schéma à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
-   Sélectionnez le type de contrat **Service (opération entrante)**.  
  
-   Génération du schéma pour le **interrogation** opération sur la table d’interface MS_SAMPLE_EMPLOYEE. Vous pouvez sélectionner l’opération et la table d’interface à partir de la **vue basée sur l’Application** nœud ou la **artefact-vue** nœud.  
  
 Pour plus d’informations sur la génération de schéma, consultez [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
## <a name="building-and-deploying-the-biztalk-project"></a>Générer et déployer le projet BizTalk  
 Vous devez maintenant générer la solution BizTalk et déployez-le sur un serveur BizTalk Server. Pour plus d’informations sur le déploiement de la solution à BizTalk Server, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’application est répertoriée sous le **Applications** nœud dans la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Dans le cadre de la configuration de l’application, vous devez créer un port de réception et un port d’envoi dans l’application et ajouter ensuite le filtre au port d’envoi afin que tous les messages du port de réception sont acheminées vers le port d’envoi.  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Création de ports d’envoi et de réception.  
  
### <a name="creating-a-receive-port"></a>Création d'un port de réception  
 Vous devez créer un WCF-Custom ou WCF-OracleEBS à sens unique port de réception, qui interroge Oracle à l’aide de l’instruction SELECT spécifiée pour le **PollingInput** propriété de liaison. Pour plus d’informations sur la création des ports de réception, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md). Lors de la création du port de réception, assurez-vous de que spécifier les propriétés suivantes de la liaison.  
  
 **Pour l’interrogation**  
  
|Propriété de liaison|Valeur|  
|----------------------|-----------|  
|**InboundOperationType**|Affectez la valeur **d’interrogation**.|  
|**PolledDataAvailableStatement**|Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE`|  
|**PollingAction**|L’action d’interrogation de récupérer à partir du schéma généré pour le **interrogation** dans la table d’interface MS_SAMPLE_EMPLOYEE. Pour cet exemple, affectez à cette propriété de liaison **InterfaceTables/interrogation/trver aide/applications/MS_SAMPLE_EMPLOYEE**.|  
|**PollingInput**|Pour cette propriété de liaison, spécifiez une instruction SELECT pour récupérer tous les enregistrements de la table d’interface MS_SAMPLE_EMPLOYEE. Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE`|  
|**PostPollStatement**|Spécifiez l’instruction après interrogation pour supprimer toutes les données à partir de la table d’interface MS_SAMPLE_EMPLOYEE. Pour cet exemple, définissez cette propriété de liaison sur :<br /><br /> `DELETE FROM MS_SAMPLE_EMPLOYEE`|  
  
 **Pour définir le contexte de l’Application**  
  
 Si vous effectuez une opération sur les artefacts d’Oracle E-Business Suite, vous devez spécifier des valeurs pour les propriétés de la liaison appropriée définir le contexte de l’application. Pour plus d’informations sur le contexte de l’application et les propriétés de liaison requises pour le contexte de l’application de paramètre, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
 Pour cet exemple, spécifiez les valeurs appropriées pour le **oracleUserName**, **oraclePassword**, et **oracleEBSResponsibility** propriétés de liaison.  
  
> [!NOTE]
>  Nous vous recommandons de configurer le niveau d’isolation de transaction et le délai d’attente de transaction lors de l’exécution d’opérations entrantes à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Vous pouvez le faire en ajoutant le comportement de service lors de la configuration du port de réception. Pour obtenir des instructions sur la façon d’ajouter le comportement de service, consultez [configurer au niveau d’Isolation de Transaction et le délai d’attente de Transaction avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).  
  
### <a name="creating-a-send-port"></a>Création d'un port d'envoi  
 Définir un emplacement sur le disque dur et créer un port d’envoi de fichier correspondant où [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supprimera les messages à partir d’Oracle. Ces messages seront en réponse à l’instruction d’interrogation que vous spécifiez pour le port de réception. Pour plus d’informations sur la création de ports d’envoi, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md).  
  
 Vous devez également ajouter un filtre sur le port d’envoi pour router les messages à partir de l’emplacement de réception. Pour ajouter le filtre au port d’envoi :  
  
1.  Double-cliquez sur le port d’envoi pour ouvrir la **propriétés de Port d’envoi** boîte de dialogue.  
  
2.  Dans le **propriétés de Port d’envoi** boîte de dialogue, cliquez sur le **filtres** onglet.  
  
3.  Spécifiez les valeurs suivantes :  
  
    -   Dans le **propriété** , cliquez sur **BTS. ReceivePortName**.  
  
    -   Dans le **opérateur** , cliquez sur  **==** .  
  
    -   Dans le **valeur** champ, spécifiez le nom de port de réception.  
  
4.  Dans le **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk permettant l’interrogation d’Oracle E-Business Suite. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-OracleEBS à sens unique port de réception, qui interroge Oracle à l’aide de l’instruction SELECT spécifiée pour le **PollingInput** propriété, de liaison est en cours d’exécution.  
  
-   Le port d’envoi de fichier qui reçoit des messages à partir de la base de données Oracle, est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, l’ensemble d’actions suivantes ont lieu, dans l’ordre :  
  
-   L’adaptateur exécute le **PolledDataAvailableStatement** qui retourne une valeur positive indiquant l’adaptateur pour exécuter l’instruction spécifiée pour **PollingInput** propriété de liaison.  
  
-   L’adaptateur exécute l’instruction SELECT pour le **PollingInput** liaison de propriété et retourne toutes les lignes dans la table d’interface MS_SAMPLE_EMPLOYEE. La réponse à partir d’Oracle E-Business Suite ressemble à ceci :  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Poll xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">   
      <DATA>   
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         <EMP_NO>10002</EMP_NO>   
         <NAME>JEFF PRICE</NAME>   
         <DESIGNATION>MANAGER</DESIGNATION>   
         <SALARY>25000</SALARY>   
         <JOIN_DATE>2007-12-15T00:00:00</JOIN_DATE>   
        </SelectRecord>   
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         <EMP_NO>10003</EMP_NO>   
         <NAME>DON HALL</NAME>   
         <DESIGNATION>ACCOUNTANT</DESIGNATION>   
         <SALARY>12000</SALARY>   
         <JOIN_DATE>2005-10-29T00:00:00</JOIN_DATE>   
        </SelectRecord>   
        …        
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         …   
        </SelectRecord>   
        …   
      </DATA>   
    </Poll>  
    ```  
  
-   L’adaptateur exécute l’instruction après interrogation, ce qui supprime toutes les données à partir de la table d’interface MS_SAMPLE_EMPLOYEE.  
  
-   Après l’intervalle d’interrogation, l’adaptateur s’exécute à nouveau **PolledDataAvailableStatement**. Étant donné que la table d’interface MS_SAMPLE_EMPLOYEE comporte pas d’enregistrement maintenant, **PolledDataAvailableStatement** ne retourne pas une valeur positive et par conséquent, l’adaptateur ne s’exécute pas l’instruction spécifiée pour le  **PollingInput** propriété de liaison. Par conséquent, client de carte n’obtient pas de tout message d’interrogation.  
  
-   Le client de carte n’obtiendra pas plus de messages d’interrogation jusqu'à ce que des enregistrements sont insérés explicitement dans la table d’interface MS_SAMPLE_EMPLOYEE. Pour insérer des enregistrements de plus, vous pouvez exécuter le script insert_apps_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, lors du prochain **PolledDataAvailableStatement** est exécutée, elle retourne une valeur positive. Par conséquent, l’adaptateur exécute l’instruction d’interrogation et les clients de carte à nouveau un message d’interrogation.  
  
> [!NOTE]
>  Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] continue à interroger jusqu'à ce que vous désactiviez explicitement le port de réception à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi et ports de réception. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation d’Oracle E-Business Suite à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)