---
title: "À l’aide de BizUnit et LoadGen pour automatiser le test de performances et stabilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c2a97a-6256-4010-8374-433017cb15d4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e84fcd29af6b698713623fbca556d988e037d8c1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-bizunit-and-loadgen-to-automate-performance-and-stability-testing"></a>À l’aide de BizUnit et LoadGen pour automatiser le test de performances et stabilité
Cette rubrique fournit des informations sur l’utilisation de l’outil Microsoft BizTalk LoadGen 2007 avec BizUnit pour automatiser le test de performances et stabilité d’une solution BizTalk Server.  
  
## <a name="biztalk-server-performance-testing-step-by-step"></a>Performances de BizTalk Server test, étape par étape  
 Avant d’examiner comment automatiser le test des performances de BizTalk Server, il est utile de connaître les étapes sont généralement effectuées dans un test de performances. Les étapes suivantes sont représentatives d’un processus de test des performances de BizTalk Server « typical » :  
  
1.  Créez un répertoire de résultats de test pour stocker les résultats et les données collectées, par exemple, les journaux des événements, les journaux de suivi, données de l’Analyseur de performances.  
  
2.  Effacer les journaux des événements sur tous les serveurs au sein de l’environnement de test.  
  
3.  Arrêtez toutes les instances d’hôte BizTalk.  
  
4.  Arrêtez toutes les instances IIS sont en cours d’exécution des hôtes BizTalk isolés tels que les gestionnaires d’adaptateur de réception SOAP et HTTP.  
  
5.  Redémarrez toutes les instances de SQL Server utilisée par les ordinateurs exécutant BizTalk Server.  
  
6.  Nettoyer la base de données MessageBox pour vous assurer qu’il n’existe pas de données restants à partir des précédentes exécutions de tests. Ceci est important, car toutes les données sont étirées peuvent fausser les résultats de test.  
  
7.  Démarrez les instances d’hôte BizTalk.  
  
8.  Démarrer les compteurs de l’Analyseur de performances pertinents sur tous les serveurs dans l’environnement de test.  
  
9. Envoyer des messages « amorcer » dans le système pour initialiser le met en cache du système.  
  
10. Une fois que les messages d’amorçage ont été traitées, effectuer le suivi de l’heure de début de test dans une base de données des résultats de test SQL Server.  
  
11. Démarrer le test de performances en démarrant à tous les agents de test LoadGen.  
  
12. Attendez que le test de fin : souvent cela systématiquement en mesurant la valeur d’un compteur de l’Analyseur de performances, notamment la longueur de file d’attente hôte.  
  
13. Heure de fin de test suivi d’un test SQL entraîne la base de données.  
  
14. Désactiver les compteurs de l’Analyseur de performances pertinents sur tous les serveurs dans l’environnement de test.  
  
15. Enregistrer les données de test dans le répertoire de résultats de test qui a été créé précédemment.  
  
16. Effectuer tout nettoyage nécessaire pour la prochaine exécution de test.  
  
 Chaque une des étapes répertoriées ci-dessus peut être automatisée à l’aide de BizUnit. En utilisant un existant actifs d’étape de test BizUnit fournit, vous pouvez rapidement et facilement générer un test de performances automatisés pour une solution BizTalk Server. Un des principaux avantages de l’automatisation des tests à l’aide de BizUnit de performances est la possibilité d’exécuter des tests pendant la nuit, ce qui signifie que les résultats sont prêtes pour l’analyse du matin. Cela réduit considérablement la charge du test de performances sur une équipe de projet.  
  
## <a name="the-microsoft-biztalk-loadgen-2007-tool"></a>L’outil Microsoft BizTalk LoadGen 2007  
 L’outil Microsoft BizTalk LoadGen 2007 (LoadGen) est un outil qui a été développé par l’équipe de test des performances et de contrainte dans le groupe de produits BizTalk Server 2006 de test de charge. LoadGen a été conçu pour définir les tests de charge de simuler les volumes de message de niveau production rapide, simple et fiable. LoadGen est multithread, de configuration et prend en charge de plusieurs transports. Le groupe de produits BizTalk utilise LoadGen quotidiennement ; Par conséquent, vous pouvez avoir un degré élevé de fiabilité que l’outil est fiable, adaptée à l’objectif et capable de simuler un large éventail de scénarios de BizTalk.  
  
 LoadGen utilise une conception modulaire qui se compose de trois couches : **présentation**, **framework** et **composant**. La couche de présentation se compose d’un pilote de ligne de commande, qui est responsable de l’infrastructure. La couche de framework lit un fichier de configuration, puis exécute les composants qui y sont spécifiés. La couche de composant se compose de trois types de composants : **charger générateurs**, **créateurs de message** et **limiter les contrôleurs**. Chacun de ces composants est extensible, afin de pouvoir créer les vôtres et les incorporer LoadGen pour répondre aux besoins de votre scénario. Étant donné que l’outil LoadGen a été développé par le groupe de produits BizTalk Server, vous devez rechercher que les composants out of box effectuera la plupart de vos besoins de test de charge. Chacun de ces composants est décrite plus en détail ici.  
  
-   **Charger les générateurs de** est responsable de la transmission des messages via un transport particulier. Générateurs de charge sont fournis pour les transports suivants :  
  
    -   Fichier  
  
    -   HTTP  
  
    -   MQSeries  
  
    -   MSMQLarge  
  
    -   MSMQ  
  
    -   SOAP  
  
    -   Web Services Enhancements (WSE)  
  
    -   Windows SharePoint Services (WSS)  
  
    -   Windows Communication Foundation (WCF)  
  
-   **Créateurs de message** sont un composant facultatif qui peut être utilisé lorsque vous avez besoin générer des messages qui contiennent des données uniques. Les créateurs de message utilisent un des deux modes de création ; synchrone et asynchrone. Si le mode de création de messages synchrone est spécifié, LoadGen utilise un seul thread pour créer des messages pour vous assurer que chaque message contienne une charge utile unique. Alors que le mode synchrone garantit des données uniques au sein de chaque message, ce mode limite également l’évolutivité. LoadGen fournit également aux créateurs de messages asynchrones qui utilisent plusieurs threads d’exécution ; Cela permet de LoadGen répondre à la vitesse de messages cible (car il peut simplement créer plus de threads). En mode asynchrone, le créateur de message peut être configuré pour modifier les données pour chaque message de façon aléatoire. Toutefois, car elle utilise plusieurs threads, il ne garantit pas que tous les messages générés pendant le test contiendra une charge utile unique.  
  
-   **Limitation des contrôleurs de** vous assurer que les messages sont transmis à un taux stable en contrôlant les générateurs de charge pendant l’exécution du test. LoadGen expose également la limitation personnalisée, qui vous permet de contrôler le flux de messages en fonction de critères, notamment :  
  
    -   Nombre de fichiers dans un dossier  
  
    -   Nombre de lignes dans une table de base de données  
  
    -   Profondeur d’une file d’attente de messages MSMQ ou MQSeries  
  
 Microsoft [outil BizTalk LoadGen 2007](http://go.microsoft.com/fwlink/?LinkId=59841) est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841).  
  
### <a name="sample-loadgen-configuration-file"></a>Exemple de fichier de configuration LoadGen  
 Toutes les informations de configuration de LoadGen sont stockées dans un fichier xml. Le fichier de configuration LoadGen contient un \<CommonSection\> élément qui configure les paramètres par défaut pour toutes les tâches de LoadGen dans le scénario LoadGen. Le fichier de configuration LoadGen peut également contenir un ou plusieurs \<Section\> éléments qui fournissent des paramètres de configuration pour une tâche LoadGen spécifique. Entrées dans un \<Section\> élément remplacent les valeurs par défaut spécifiées dans le \<CommonSection\> élément.  
  
 L’exemple de fichier de configuration LoadGen qui suit est une version légèrement modifiée du fichier de configuration d’exemple FileToFileLG.xml qui est inclus dans le sous-répertoire \ConfigFiles\ConsoleConfigFiles du répertoire d’installation LoadGen. Ce test envoie des 25 messages \<LotSizePerInterval\> toutes les 200 millisecondes \<SleepInterval\>, 5 threads par le Générateur de charge \<NumThreadsperSection\>et s’arrête à la charge tester après leur 5000 messages \<%NUMFILES\> ont été envoyés.  
  
 Le contrôleur de limitation de fichier est spécifié dans le \<ThrottleController\> section. La valeur de \<ThresholdRange\> a la valeur 1000 à 2000, ce qui signifie que si l’emplacement du fichier C:\Scenarios\FileToFile\Receive (paramètres) a moins de 1 000 ou plus de 2000 fichiers, le contrôleur de limitation accélèrera le fichier Générateur et augmenter/diminuer la charge selon le cas. Le nombre de fichiers dans l’emplacement du fichier sera vérifiée toutes les 1000 millisecondes \<SleepInterval\>. Le \<FileSection\> élément définit les propriétés pour les messages envoyés par les générateurs de charge. Le fichier FileToFileLG.xml \<SrcFilePath\> LoadGen seront copiés vers le filedrop C:\Scenarios\FileToFile\Receive \<DstFilePath >. Le transport de fichier est utilisé ici, car il s’agit du transport par défaut spécifié dans le \<nom Transport\> élément dans le \<CommonSection\> élément.  
  
```  
<LoadGenFramework>  
   <CommonSection>  
      <LoadGenVersion>2</LoadGenVersion>  
      <OptimizeLimitFileSize>204800</OptimizeLimitFileSize>  
      <NumThreadsPerSection>5</NumThreadsPerSection>  
      <SleepInterval>200</SleepInterval>  
      <LotSizePerInterval>25</LotSizePerInterval>  
      <RetryInterval>10000</RetryInterval>  
      <StopMode Mode="Files">  
         <NumFiles>5000</NumFiles>  
      </StopMode>  
      <Transport Name="FILE">  
         <Assembly>FileTransport.dll/FileTransport.FileTransport</Assembly>  
      </Transport>  
      <ThrottleController Mode="Custom">  
         <Monitor Name="File">  
            <Assembly>FileMonitor.dll/DropLocationFileMonitor.DropLocationFileMonitor</Assembly>  
            <ThresholdRange>1000-2000</ThresholdRange>  
            <SleepInterval>1000</SleepInterval>  
            <Parameters>C:\Scenarios\FileToFile\Receive</Parameters>  
         </Monitor>  
         <ThrottleCondition>File</ThrottleCondition>  
      </ThrottleController>  
   </CommonSection>  
   <Section Name="FileSection">  
      <SrcFilePath>C:\LoadGen\ConfigFiles\ConsoleConfigFiles\FileToFileLG.xml</SrcFilePath>  
      <DstLocation>  
         <Parameters>  
            <DstFilePath>C:\Scenarios\FileToFile\Receive</DstFilePath>  
         </Parameters>  
      </DstLocation>  
   </Section>  
</LoadGenFramework>  
```  
  
### <a name="using-bizunit-to-drive-loadgen"></a>À l’aide de BizUnit au lecteur LoadGen  
 BizUnit fournit le **LoadGenExecuteStep** pour faciliter automatisée des performances et la stabilité du test. Le **TestExecution** étape d’un exemple de fichier de configuration BizUnit qui utilise **LoadGenExecuteStep** est indiqué dans l’exemple de code suivant. Notez que cette étape accepte un seul paramètre de configuration, qui est l’emplacement du fichier de configuration LoadGen.  
  
```  
<TestCase testName="Test_LoadGen">  
   <TestSetup>  
   </TestSetup>  
   <TestExecution>  
      <TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
         <LoadGenTestConfig>..\..\..\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
      </TestStep>  
   </TestExecution>  
   <!-- Test cleanup: test cases should always leave the system in the state they found it -->  
   <TestCleanup>  
   </TestCleanup>  
</TestCase>  
```  
  
 Le reste de cette rubrique décrit le fichier de configuration pour un cas de test BizUnit qui automatise les tests de performances avec l’outil LoadGen.  
  
> [!NOTE]  
>  Ce fichier de configuration peut être utilisé en tant que modèle à intégrer rapidement BizUnit et LoadGen dans le cadre de vos tests de performances. Avant d’exécuter ce cas de test, vous devez personnaliser le fichier de configuration pour votre environnement. Les sections du fichier de configuration qui doivent être personnalisés sont indiquées en conséquence.  
  
 Pour commencer, spécifiez une valeur pour le **testName** paramètre approprié pour la solution BizTalk.  
  
```  
<TestCase testName="Performance-Guide-Sample-Loadgen-Test">  
```  
  
 Puis ajoutez les variables de contexte à la **TestSetup** étape. Ces variables de contexte seront référencés dans l’ensemble de la durée du cas de test. Pour utiliser ce fichier de configuration, modifiez les valeurs spécifiées pour **TestCaseResultsDir** (C:\Dev Work\Perf Guide Demos\PerfResults\\) et **ordinateur** (BIZTALKADMIN01) pour faire correspondre votre environnement.  
  
```  
<TestSetup>  
   <!-- Context property: name of test run -->  
   <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
      <ContextItem contextKey="TestRunName">  
         <ItemTest takeFromCtx="BizUnitTestCaseName"></ItemTest>  
         <ItemTest>_%DateTime%</ItemTest>  
      </ContextItem>  
   </TestStep>  
   <!-- Context property: name of test directory to store results -->  
   <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
      <ContextItem contextKey="TestCaseResultsDir">  
         <ItemTest>C:\Dev Work\Perf Guide Demos\PerfResults\</ItemTest>  
         <ItemTest takeFromCtx="TestRunName"></ItemTest>  
      </ContextItem>  
   </TestStep>  
   <!-- Context property: perfmon log file -->  
   <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
      <ContextItem contextKey="PerfMonFilePath">  
         <ItemTest takeFromCtx="TestCaseResultsDir"></ItemTest>  
         <ItemTest>\PerfCounters.blg</ItemTest>  
      </ContextItem>  
   </TestStep>  
   <!-- Context property: destintation for app event log on test computer -->  
   <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
      <ContextItem contextKey="DestPath- BIZTALKADMIN01-AppEventLog">  
         <ItemTest takeFromCtx="TestCaseResultsDir"></ItemTest>  
         <ItemTest> BIZTALKADMIN01_ApplicationLog.evt</ItemTest>  
      </ContextItem>  
   </TestStep>  
   <!-- Clear the application event log on test computer -->  
   <TestStep assemblyPath="" typeName="BizUnit.EventLogClearStep">  
      <Machine>BIZTALKADMIN01</Machine>  
      <EventLog>Application</EventLog>  
   </TestStep>  
   <!-- Create the directory to save all the test results -->  
   <TestStep assemblyPath="" typeName="BizUnit.CreateDirectory">  
      <DirectoryName takeFromCtx="TestCaseResultsDir" ></DirectoryName>  
   </TestStep>  
</TestSetup>  
```  
  
 Après avoir effectué la **TestSetup** étape, nous permet d’entrer le **TestExecution** étape. La première étape consiste à arrêter les instances d’hôte BizTalk. Distinct **BizUnit.HostConductorStep** section doit être ajoutée pour chaque instance d’hôte distinctes. Si vous utilisez ce fichier de configuration dans votre environnement, vous devez également entrer les valeurs appropriées pour **HostInstanceName**, **Server**, **ouverture de session**et  **Mot de passe**.  
  
```  
<TestExecution>  
   <!-- Step 1: Stop BizTalk Hosts -->  
   <TestStep assemblyPath="" typeName="BizUnit.HostConductorStep, BizUnit.BizTalkSteps">  
      <Action>stop</Action>  
      <HostInstanceName>BizTalkServerApplication</HostInstanceName>  
      <Server>BizTalkAdmin01</Server>  
      <Logon>ServerName\Administrator</Logon>  
      <PassWord>Pass@word1</PassWord>  
      <GrantLogOnAsService>true</GrantLogOnAsService>  
   </TestStep>  
```  
  
 Après l’arrêt de toutes les instances d’hôte, nous nettoyer la base de données BizTalk MessageBox à l’aide de la bts_CleanupMsgBox procédure stockée. Pour utiliser cette étape, vous devez modifier la valeur de **ConnectionString** pour correspondre à votre environnement.  
  
```  
<!-- Step 2: Clean Up MessageBox -->  
<TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
   <DelayBeforeExecution>1</DelayBeforeExecution>  
   <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=BizTalkMsgBoxDb;server=BIZTALKADMIN01;Connect Timeout=30</ConnectionString>  
   <SQLQuery>  
      <RawSQLQuery>[dbo].[bts_CleanupMsgbox]</RawSQLQuery>  
   </SQLQuery>  
</TestStep>  
```  
  
 Étape 3 de la **TestExecution** étape démarre les compteurs de l’Analyseur de performances (PerfMon) qui sont spécifiés dans un fichier de modèle. Un exemple de fichier de modèle est répertorié sous l’exemple **BizUnit.PerfmonCountersStep** ci-dessous. Pour utiliser le fichier de modèle, vous devez modifier la valeur spécifiée pour **CountersListFilePath** à votre environnement. Modifier le fichier de modèle du compteur exemple performances moniteur pour inclure des compteurs PerfMon que vous souhaitez analyser ou supprimez ceux qui ne sont pas pertinentes pour votre scénario.  
  
```  
<!-- Step 3: Start Perfmon counters -->  
<TestStep assemblyPath="" typeName="BizUnit.PerfmonCountersStep">  
   <PerfmonAction>Start</PerfmonAction>  
   <CounterSetName>PerfGuidePerfmonCounters</CounterSetName>  
   <CountersListFilePath>C:\Dev Work\Perf Guide Demos\Test_06_PerfCounters.txt</CountersListFilePath>  
   <SampleInterval>5</SampleInterval>  
   <PerfmonLogFilePath takeFromCtx="PerfMonFilePath"></PerfmonLogFilePath>  
</TestStep>  
```  
  
 **Fichier modèle de compteur d’analyseur de performances exemple (Test_06_PerfCounters.txt référencé par le BizUnit.PerfmonCountersStep) :**  
  
```  
\Processor(*)\*  
\Process(*)\*  
\Memory\*  
\PhysicalDisk(*)\*  
\System\Context Switches/sec  
\System\Processor Queue Length  
\BizTalk:FILE Receive Adapter(*)\*  
\BizTalk:File Send Adapter(*)\*  
\BizTalk:FTP Receive Adapter(*)\*  
\BizTalk:FTP Send Adapter(*)\*  
\BizTalk:HTTP Receive Adapter(*)\*  
\BizTalk:HTTP Send Adapter(*)\*  
\BizTalk:Message Agent(*)\*  
\BizTalk:Messaging(*)\*  
\BizTalk:Message Box:General Counters(*)\*  
\BizTalk:Message Box:Host Counters(*)\*  
\BizTalk:Messaging Latency(*)\*  
\BizTalk:SOAP Receive Adapter(*)\*  
\BizTalk:SOAP Send Adapter(*)\*  
\BizTalk:TDDS(*)\*  
\XLANG/s Orchestrations(*)\*  
```  
  
 Maintenant, nous allons commencer les instances d’hôte BizTalk Server. Distinct **BizUnit.HostConductorStep** section doit être ajoutée pour chaque instance d’hôte distinctes (distinct inclut plusieurs instances d’un ordinateur hôte sur les serveurs). Si vous utilisez ce fichier de configuration dans votre environnement, vous devez également entrer les valeurs appropriées pour **HostInstanceName**, **Server**, **ouverture de session**et  **Mot de passe**.  
  
```  
<!-- Step 4: Start BizTalk Hosts -->  
<TestStep assemblyPath="" typeName="BizUnit.BizTalkSteps.HostConductorStep, BizUnit.BizTalkSteps, Version=3.0.0.0, Culture=neutral, PublicKeyToken=7eb7d82981ae5162">  
   <Action>start</Action>  
   <HostInstanceName>BizTalkServerApplication</HostInstanceName>  
   <Server>BizTalkAdmin01</Server>  
   <Logon>ServerName\Administrator</Logon>  
   <PassWord>Pass@word1</PassWord>  
   <GrantLogOnAsService>true</GrantLogOnAsService>  
</TestStep>  
```  
  
 Étape 5 » primes « le système en envoyant des deux messages à l’aide de BizTalk Server **BizUnit.LoadGenExecuteStep**; modifier la valeur de la **LoadGenTestConfig** paramètre à votre environnement.  
  
```  
<!-- Step 5: Send Priming messages -->  
<TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
   <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
</TestStep>  
```  
  
 Étape 6 a écrit le fichier de configuration LoadGen dans la mémoire afin qu’il peut ensuite être écrit à la base de données des résultats de test lorsque le test est terminé.  
  
```  
  
      <!-- Step 6: Read loadgen file into context variable -->  
<TestStep assemblyPath="" typeName="BizUnit.FileReadAndLoadToContext">  
   <FilePath>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</FilePath>  
   <ContextPropertyName>LoadGenFileContent</ContextPropertyName>  
</TestStep>  
```  
  
 Maintenant, nous écrivons l’heure de début de test à une base de données des résultats de test. Modifier la **ConnectionString** et **RawSQLQuery** paramètres devant correspondre à votre environnement.  
  
```  
<!-- Step 7: Update test results DB with test start time -->  
<TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
   <DelayBeforeExecution>1</DelayBeforeExecution>  
   <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=TestResults;server=BizTalkAdmin01;Connect Timeout=30</ConnectionString>  
   <SQLQuery>  
      <RawSQLQuery>INSERT INTO tblPerformanceResults (Test_ID, StartTime,LoadGenFile) VALUES ('{0}',GetDate(),'{1}' )</RawSQLQuery>  
      <SQLQueryParams>  
         <SQLQueryParam takeFromCtx="TestRunName"></SQLQueryParam>  
         <SQLQueryParam takeFromCtx="LoadGenFileContent"></SQLQueryParam>  
      </SQLQueryParams>  
   </SQLQuery>  
</TestStep>  
```  
  
 Étape 8 est où le test de performances réel est lancée à l’aide de **BizUnit.LoadGenExecuteStep**. Cette étape spécifie le même fichier de configuration LoadGen a été utilisé à l’étape 5, mais vous pouvez spécifier n’importe quel fichier de configuration LoadGen valide ici. **BizUnit.DelayStep** est utilisé à l’étape 9 pour imposer un délai de 5 secondes pour laisser le temps pour les messages à circuler via le système. Longueur de file d’attente hôte est calculée à l’aide de **BizUnit.PerMonCounterMonitorStep**. Lorsque ce paramètre atteint la valeur 1 comme indiqué dans l’étape 10, le test est terminé. Modifier les valeurs pour le **InstanceName** et **Server** paramètres correspondre au nom de l’instance de l’hôte et le serveur que vous souhaitez surveiller dans votre environnement.  
  
```  
<!-- Step 8: LoadGen: Load actual perf test -->  
<TestStep assemblyPath="" typeName="BizUnit.LoadGenSteps.LoadGenExecuteStep, BizUnit.LoadGenSteps , Version=3.0.0.0, Culture=neutral, PublicKeyToken=7eb7d82981ae5162">  
   <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
</TestStep>  
<!-- Step 9: Delay for 5 secs to allow msgs to start flowing -->  
<TestStep assemblyPath="" typeName="BizUnit.DelayStep">  
   <Delay>5000</Delay>  
</TestStep>  
<!-- Step 10: Wait for Orch Host Queue depth to reach one -->  
<TestStep assemblyPath="" typeName="BizUnit.PerfMonCounterMonitorStep">  
   <CategoryName>BizTalk:Message Box:Host Counters</CategoryName>  
   <CounterName>Host Queue - Length</CounterName>  
   <InstanceName>BizTalkServerApplication:biztalkmsgboxdb:BizTalkAdmin01</InstanceName>  
   <Server>BizTalkAdmin01</Server>  
   <CounterTargetValue>1</CounterTargetValue>  
</TestStep>  
```  
  
 À la fin du test, nous utilisons **BizUnit.DBExecuteNonQueryStep** pour mettre à jour la base de données des résultats de test. Issue de cette étape correspond à la fin de l’étape d’exécution du test, comme indiqué par la fermeture \</TestExecution\> balise. Là encore, vous devez modifier le **ConnectionString** et **RawSQLQuery** paramètres devant correspondre à votre environnement.  
  
```  
   <!-- Step 11: Update test results DB with test stop time -->  
   <TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
      <DelayBeforeExecution>1</DelayBeforeExecution>  
      <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=TestResults;server=BIZTALKADMIN01;Connect Timeout=30</ConnectionString>  
      <SQLQuery>  
         <RawSQLQuery>UPDATE tblPerformanceResults SET EndTime = GetDate() WHERE Test_ID = '{0}'</RawSQLQuery>  
         <SQLQueryParams>  
            <SQLQueryParam takeFromCtx="TestRunName"></SQLQueryParam>  
         </SQLQueryParams>  
      </SQLQuery>  
   </TestStep>  
</TestExecution>  
```  
  
 Entrez l’étape de nettoyage de test lors de la conclusion de l’étape d’exécution. Cette étape utilise **BizUnit.PerfmonCountersStep** pour désactiver les compteurs de l’Analyseur de performances qui ont été démarrées précédemment (à l’étape 3).  
  
```  
<TestCleanup>  
      <!-- Return system to state prior to test -->  
      <!-- Stop perfmon counters -->  
      <TestStep assemblyPath="" typeName="BizUnit.PerfmonCountersStep" failOnError="false">  
         <PerfmonAction>Stop</PerfmonAction>  
         <CounterSetName>PerfGuidePerfmonCounters</CounterSetName>  
      </TestStep>  
   </TestCleanup>  
</TestCase>  
```  
  
 Cet exemple illustre comment BizUnit peut être combinée avec l’outil LoadGen pour automatiser le test de performances. Le test de charge décrit par le fichier de configuration BizUnit peut être exécuté à partir des outils de test de Visual Studio, dans la même manière que les tests fonctionnels. Adoptant cette approche vous permet de gérer, administrer et collecter des données pour vos tests de performances de manière centralisée.  
  
 À l’aide de BizUnit et LoadGen dans une approche automatisée, il est très facile à planifier plusieurs séries de tests qui se produirait hors des heures, ce qui fournissent des résultats des tests suffisamment pour l’analyse pendant les heures de travail normales. Lors de l’automatisation des tests de performances, envisagez d’utiliser des scripts de LoadGen que modèle différentes charges par le système, par exemple vous pouvez souhaiter simuler des degrés divers (75 % et 100 % de 125 %) du volume de message de production prévu. Lorsque vous effectuez le test de charge, il est particulièrement important de tester la surcharge ou le scénario de « journée incorrect ». Avant de placer le système en production, vous devez savoir quel est le débit maximal acceptable (MST) pour chaque cas de test dans l’environnement BizTalk Server. Pour plus d’informations sur les performances maximales admissibles, consultez [Nouveautés des performances durables ?](http://go.microsoft.com/fwlink/?LinkID=132304) (http://go.microsoft.com/fwlink/?LinkID=132304) dans la documentation de BizTalk Server 2009.  
  
### <a name="the-complete-bizunit-loadgen-sample-configuration-file"></a>Le fichier de configuration d’exemple BizUnit LoadGen terminé  
 La liste suivante contient tout le contenu du fichier de configuration BizUnit mentionnés précédemment.  
  
```  
<TestCase testName="Performance-Guide-Sample-Loadgen-Test">  
   <TestSetup>  
      <!-- Context property: name of test run -->  
      <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
         <ContextItem contextKey="TestRunName">  
            <ItemTest takeFromCtx="BizUnitTestCaseName"></ItemTest>  
            <ItemTest>_%DateTime%</ItemTest>  
         </ContextItem>  
      </TestStep>  
      <!-- Context property: name of test directory to store results -->  
      <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
         <ContextItem contextKey="TestCaseResultsDir">  
            <ItemTest>C:\Dev Work\Perf Guide Demos\PerfResults\</ItemTest>  
            <ItemTest takeFromCtx="TestRunName"></ItemTest>  
         </ContextItem>  
      </TestStep>  
      <!-- Context property: perfmon log file -->  
      <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
         <ContextItem contextKey="PerfMonFilePath">  
            <ItemTest takeFromCtx="TestCaseResultsDir"></ItemTest>  
            <ItemTest>\PerfCounters.blg</ItemTest>  
         </ContextItem>  
      </TestStep>  
      <!-- Context property: destintation for app event log on BTSSVR-001 -->  
      <TestStep assemblyPath="" typeName="BizUnit.ContextManipulatorStep">  
         <ContextItem contextKey="DestPath-BTSSVR-001-AppEventLog">  
            <ItemTest takeFromCtx="TestCaseResultsDir"></ItemTest>  
            <ItemTest>BTSSVR-001_ApplicationLog.evt</ItemTest>  
         </ContextItem>  
      </TestStep>  
      <!-- Clear the application event log on BTSSVR-001 -->  
      <TestStep assemblyPath="" typeName="BizUnit.EventLogClearStep">  
         <Machine>BIZTALKADMIN01</Machine>  
         <EventLog>Application</EventLog>  
      </TestStep>  
      <!-- Create the directory to save all the test results -->  
      <TestStep assemblyPath="" typeName="BizUnit.CreateDirectory">  
         <DirectoryName takeFromCtx="TestCaseResultsDir" ></DirectoryName>  
      </TestStep>  
   </TestSetup>  
  
   <TestExecution>  
      <!-- Step 1: Stop BizTalk Hosts -->  
      <TestStep assemblyPath="" typeName="BizUnit.HostConductorStep, BizUnit.BizTalkSteps">  
         <Action>stop</Action>  
         <HostInstanceName>BizTalkServerApplication</HostInstanceName>  
         <Server>BizTalkAdmin01</Server>  
         <Logon>ServerName\Administrator</Logon>  
         <PassWord>Pass@word1</PassWord>  
         <GrantLogOnAsService>true</GrantLogOnAsService>  
      </TestStep>  
      <!-- Step 2: Clean Up MessageBox -->  
      <TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
         <DelayBeforeExecution>1</DelayBeforeExecution>  
         <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=BizTalkMsgBoxDb;server=BIZTALKADMIN01;Connect Timeout=30</ConnectionString>  
         <SQLQuery>  
            <RawSQLQuery>[dbo].[bts_CleanupMsgbox]</RawSQLQuery>  
         </SQLQuery>  
      </TestStep>  
      <!-- Step 3: Start Perfmon counters -->  
      <TestStep assemblyPath="" typeName="BizUnit.PerfmonCountersStep">  
         <PerfmonAction>Start</PerfmonAction>  
         <CounterSetName>PerfGuidePerfmonCounters</CounterSetName>  
         <CountersListFilePath>C:\Dev Work\Perf Guide Demos\Test_06_PerfCounters.txt</CountersListFilePath>  
         <SampleInterval>5</SampleInterval>  
         <PerfmonLogFilePath takeFromCtx="PerfMonFilePath"></PerfmonLogFilePath>  
      </TestStep>  
      <!-- Step 4: Start BizTalk Hosts -->  
      <TestStep assemblyPath="" typeName="BizUnit.BizTalkSteps.HostConductorStep, BizUnit.BizTalkSteps, Version=3.0.0.0, Culture=neutral, PublicKeyToken=7eb7d82981ae5162">  
         <Action>start</Action>  
         <HostInstanceName>BizTalkServerApplication</HostInstanceName>  
         <Server>BizTalkAdmin01</Server>  
         <Logon>ServerName\Administrator</Logon>  
         <PassWord>Pass@word1</PassWord>  
         <GrantLogOnAsService>true</GrantLogOnAsService>  
      </TestStep>  
      <!-- Step 5: Send Priming messages -->  
      <TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
         <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
      </TestStep>  
      <!-- Step 6: Read loadgen file into context variable -->  
      <TestStep assemblyPath="" typeName="BizUnit.FileReadAndLoadToContext">  
         <FilePath>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</FilePath>  
         <ContextPropertyName>LoadGenFileContent</ContextPropertyName>  
      </TestStep>  
      <!-- Step 7: Update test results DB with test start time -->  
      <TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
         <DelayBeforeExecution>1</DelayBeforeExecution>  
         <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=TestResults;server=BizTalkAdmin01;Connect Timeout=30</ConnectionString>  
         <SQLQuery>  
            <RawSQLQuery>INSERT INTO tblPerformanceResults (Test_ID, StartTime,LoadGenFile) VALUES ('{0}',GetDate(),'{1}' )</RawSQLQuery>  
            <SQLQueryParams>  
               <SQLQueryParam takeFromCtx="TestRunName"></SQLQueryParam>  
               <SQLQueryParam takeFromCtx="LoadGenFileContent"></SQLQueryParam>  
            </SQLQueryParams>  
         </SQLQuery>  
      </TestStep>  
      <!-- Step 8: LoadGen: Load actual perf test -->  
      <TestStep assemblyPath="" typeName="BizUnit.LoadGenSteps.LoadGenExecuteStep, BizUnit.LoadGenSteps , Version=3.0.0.0, Culture=neutral, PublicKeyToken=7eb7d82981ae5162">  
        <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
      </TestStep>  
      <!-- Step 9: Delay for 5 secs to allow msgs to start flowing -->  
      <TestStep assemblyPath="" typeName="BizUnit.DelayStep">  
         <Delay>5000</Delay>  
      </TestStep>  
      <!-- Step 10: Wait for Orch Host Queue depth to reach one -->  
      <TestStep assemblyPath="" typeName="BizUnit.PerfMonCounterMonitorStep">  
         <CategoryName>BizTalk:Message Box:Host Counters</CategoryName>  
         <CounterName>Host Queue - Length</CounterName>  
         <InstanceName>BizTalkServerApplication:biztalkmsgboxdb:BizTalkAdmin01</InstanceName>  
         <Server>BizTalkAdmin01</Server>  
         <CounterTargetValue>1</CounterTargetValue>  
      </TestStep>  
      <!-- Step 11: Update test results DB with test stop time -->  
      <TestStep assemblyPath="" typeName="BizUnit.DBExecuteNonQueryStep">  
         <DelayBeforeExecution>1</DelayBeforeExecution>  
         <ConnectionString>Persist Security Info=False;Integrated Security=SSPI;database=TestResults;server=BIZTALKADMIN01;Connect Timeout=30</ConnectionString>  
         <SQLQuery>  
            <RawSQLQuery>UPDATE tblPerformanceResults SET EndTime = GetDate() WHERE Test_ID = '{0}'</RawSQLQuery>  
            <SQLQueryParams>  
               <SQLQueryParam takeFromCtx="TestRunName"></SQLQueryParam>  
            </SQLQueryParams>  
         </SQLQuery>  
      </TestStep>  
   </TestExecution>  
  
   <TestCleanup>  
      <!-- Return system to state prior to test -->  
      <!-- Stop perfmon counters -->  
      <TestStep assemblyPath="" typeName="BizUnit.PerfmonCountersStep" failOnError="false">  
         <PerfmonAction>Stop</PerfmonAction>  
         <CounterSetName>PerfGuidePerfmonCounters</CounterSetName>  
      </TestStep>  
   </TestCleanup>  
</TestCase>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de BizUnit pour faciliter les tests automatisés](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)