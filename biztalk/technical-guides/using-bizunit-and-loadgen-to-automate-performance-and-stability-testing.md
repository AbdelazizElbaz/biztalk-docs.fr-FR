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
ms.openlocfilehash: 538e47f481f0817acfbd26477866a3d45a0d285b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-bizunit-and-loadgen-to-automate-performance-and-stability-testing"></a><span data-ttu-id="27f04-102">À l’aide de BizUnit et LoadGen pour automatiser le test de performances et stabilité</span><span class="sxs-lookup"><span data-stu-id="27f04-102">Using BizUnit and LoadGen to Automate Performance and Stability Testing</span></span>
<span data-ttu-id="27f04-103">Cette rubrique fournit des informations sur l’utilisation de l’outil Microsoft BizTalk LoadGen 2007 avec BizUnit pour automatiser le test de performances et stabilité d’une solution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="27f04-103">This topic provides information about how to use the Microsoft BizTalk LoadGen 2007 tool with BizUnit to automate performance and stability testing of a BizTalk Server solution.</span></span>  
  
## <a name="biztalk-server-performance-testing-step-by-step"></a><span data-ttu-id="27f04-104">Performances de BizTalk Server test, étape par étape</span><span class="sxs-lookup"><span data-stu-id="27f04-104">BizTalk Server performance testing, step-by-step</span></span>  
 <span data-ttu-id="27f04-105">Avant d’examiner comment automatiser le test des performances de BizTalk Server, il est utile de connaître les étapes sont généralement effectuées dans un test de performances.</span><span class="sxs-lookup"><span data-stu-id="27f04-105">Before investigating how to automate BizTalk Server performance testing, it is useful to know what steps are typically performed in a performance test.</span></span> <span data-ttu-id="27f04-106">Les étapes suivantes sont représentatives d’un processus de test des performances de BizTalk Server « typical » :</span><span class="sxs-lookup"><span data-stu-id="27f04-106">The following steps are representative of a “typical” BizTalk Server performance testing process:</span></span>  
  
1.  <span data-ttu-id="27f04-107">Créez un répertoire de résultats de test pour stocker les résultats et les données collectées, par exemple, les journaux des événements, les journaux de suivi, données de l’Analyseur de performances.</span><span class="sxs-lookup"><span data-stu-id="27f04-107">Create a test results directory to store results and data collected, for example, event logs, trace logs, Performance Monitor data.</span></span>  
  
2.  <span data-ttu-id="27f04-108">Effacer les journaux des événements sur tous les serveurs au sein de l’environnement de test.</span><span class="sxs-lookup"><span data-stu-id="27f04-108">Clear the event logs on all servers within the test environment.</span></span>  
  
3.  <span data-ttu-id="27f04-109">Arrêtez toutes les instances d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="27f04-109">Stop all BizTalk host instances.</span></span>  
  
4.  <span data-ttu-id="27f04-110">Arrêtez toutes les instances IIS sont en cours d’exécution des hôtes BizTalk isolés tels que les gestionnaires d’adaptateur de réception SOAP et HTTP.</span><span class="sxs-lookup"><span data-stu-id="27f04-110">Stop any IIS instances that are running isolated BizTalk hosts such as the SOAP and HTTP receive adapter handlers.</span></span>  
  
5.  <span data-ttu-id="27f04-111">Redémarrez toutes les instances de SQL Server utilisée par les ordinateurs exécutant BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="27f04-111">Restart all instances of SQL Server used by the computers running BizTalk Server.</span></span>  
  
6.  <span data-ttu-id="27f04-112">Nettoyer la base de données MessageBox pour vous assurer qu’il n’existe pas de données restants à partir des précédentes exécutions de tests.</span><span class="sxs-lookup"><span data-stu-id="27f04-112">Clean up the MessageBox database to ensure that there is no leftover data from previous tests runs.</span></span> <span data-ttu-id="27f04-113">Ceci est important, car toutes les données sont étirées peuvent fausser les résultats de test.</span><span class="sxs-lookup"><span data-stu-id="27f04-113">This is important because any leftover data could skew test results.</span></span>  
  
7.  <span data-ttu-id="27f04-114">Démarrez les instances d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="27f04-114">Start the BizTalk host instances.</span></span>  
  
8.  <span data-ttu-id="27f04-115">Démarrer les compteurs de l’Analyseur de performances pertinents sur tous les serveurs dans l’environnement de test.</span><span class="sxs-lookup"><span data-stu-id="27f04-115">Start the relevant Performance Monitor counters on all servers in the test environment.</span></span>  
  
9. <span data-ttu-id="27f04-116">Envoyer des messages « amorcer » dans le système pour initialiser le met en cache du système.</span><span class="sxs-lookup"><span data-stu-id="27f04-116">Send “priming” messages through the system to initialize the system caches.</span></span>  
  
10. <span data-ttu-id="27f04-117">Une fois que les messages d’amorçage ont été traitées, effectuer le suivi de l’heure de début de test dans une base de données des résultats de test SQL Server.</span><span class="sxs-lookup"><span data-stu-id="27f04-117">After the priming messages have been processed, track the test start time in a SQL Server test results database.</span></span>  
  
11. <span data-ttu-id="27f04-118">Démarrer le test de performances en démarrant à tous les agents de test LoadGen.</span><span class="sxs-lookup"><span data-stu-id="27f04-118">Start the performance test by starting all of the LoadGen test agents.</span></span>  
  
12. <span data-ttu-id="27f04-119">Attendez que le test de fin : souvent cela systématiquement en mesurant la valeur d’un compteur de l’Analyseur de performances, notamment la longueur de file d’attente hôte.</span><span class="sxs-lookup"><span data-stu-id="27f04-119">Wait for the test to complete – often this can be done systematically by measuring the value of a Performance Monitor counter such as host queue length.</span></span>  
  
13. <span data-ttu-id="27f04-120">Heure de fin de test suivi d’un test SQL entraîne la base de données.</span><span class="sxs-lookup"><span data-stu-id="27f04-120">Track test end time in a SQL test results database.</span></span>  
  
14. <span data-ttu-id="27f04-121">Désactiver les compteurs de l’Analyseur de performances pertinents sur tous les serveurs dans l’environnement de test.</span><span class="sxs-lookup"><span data-stu-id="27f04-121">Stop the relevant Performance Monitor counters on all servers in the test environment.</span></span>  
  
15. <span data-ttu-id="27f04-122">Enregistrer les données de test dans le répertoire de résultats de test qui a été créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="27f04-122">Save the test data to the test results directory that was created earlier.</span></span>  
  
16. <span data-ttu-id="27f04-123">Effectuer tout nettoyage nécessaire pour la prochaine exécution de test.</span><span class="sxs-lookup"><span data-stu-id="27f04-123">Perform any necessary cleanup for the next test run.</span></span>  
  
 <span data-ttu-id="27f04-124">Chaque une des étapes répertoriées ci-dessus peut être automatisée à l’aide de BizUnit.</span><span class="sxs-lookup"><span data-stu-id="27f04-124">Each and every one of the steps just listed can be automated using BizUnit.</span></span> <span data-ttu-id="27f04-125">En utilisant un existant actifs d’étape de test BizUnit fournit, vous pouvez rapidement et facilement générer un test de performances automatisés pour une solution BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="27f04-125">By utilizing the existing test step assets that BizUnit provides, you can quickly and easily generate an automated performance test for a BizTalk Server solution.</span></span> <span data-ttu-id="27f04-126">Un des principaux avantages de l’automatisation des tests à l’aide de BizUnit de performances est la possibilité d’exécuter des tests pendant la nuit, ce qui signifie que les résultats sont prêtes pour l’analyse du matin.</span><span class="sxs-lookup"><span data-stu-id="27f04-126">One of the primary benefits of automating performance testing by using BizUnit is the flexibility to run tests overnight – meaning that the results are ready for analysis in the morning.</span></span> <span data-ttu-id="27f04-127">Cela réduit considérablement la charge du test de performances sur une équipe de projet.</span><span class="sxs-lookup"><span data-stu-id="27f04-127">This greatly reduces the burden of performance testing on a project team.</span></span>  
  
## <a name="the-microsoft-biztalk-loadgen-2007-tool"></a><span data-ttu-id="27f04-128">L’outil Microsoft BizTalk LoadGen 2007</span><span class="sxs-lookup"><span data-stu-id="27f04-128">The Microsoft BizTalk LoadGen 2007 tool</span></span>  
 <span data-ttu-id="27f04-129">L’outil Microsoft BizTalk LoadGen 2007 (LoadGen) est un outil qui a été développé par l’équipe de test des performances et de contrainte dans le groupe de produits BizTalk Server 2006 de test de charge.</span><span class="sxs-lookup"><span data-stu-id="27f04-129">The BizTalk LoadGen 2007 tool (LoadGen) is a load testing tool that was developed by the Stress and Performance Testing team in the BizTalk Server 2006 product group.</span></span> <span data-ttu-id="27f04-130">LoadGen a été conçu pour définir les tests de charge de simuler les volumes de message de niveau production rapide, simple et fiable.</span><span class="sxs-lookup"><span data-stu-id="27f04-130">LoadGen was designed to quickly, easily, and reliably define load tests that simulate production level message volumes.</span></span> <span data-ttu-id="27f04-131">LoadGen est multithread, de configuration et prend en charge de plusieurs transports.</span><span class="sxs-lookup"><span data-stu-id="27f04-131">LoadGen is multi-threaded, configuration-driven, and supports multiple transports.</span></span> <span data-ttu-id="27f04-132">Le groupe de produits BizTalk utilise LoadGen quotidiennement ; Par conséquent, vous pouvez avoir un degré élevé de fiabilité que l’outil est fiable, adaptée à l’objectif et capable de simuler un large éventail de scénarios de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="27f04-132">The BizTalk product group uses LoadGen on a daily basis; therefore you can have a high degree of confidence that the tool is durable, fit for the purpose, and able to simulate a wide variety of BizTalk scenarios.</span></span>  
  
 <span data-ttu-id="27f04-133">LoadGen utilise une conception modulaire qui se compose de trois couches : **présentation**, **framework** et **composant**.</span><span class="sxs-lookup"><span data-stu-id="27f04-133">LoadGen employs a modular design that consists of three layers: **presentation**, **framework** and **component**.</span></span> <span data-ttu-id="27f04-134">La couche de présentation se compose d’un pilote de ligne de commande, qui est responsable de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="27f04-134">The presentation layer consists of a command-line driver, which is responsible for driving the framework.</span></span> <span data-ttu-id="27f04-135">La couche de framework lit un fichier de configuration, puis exécute les composants qui y sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="27f04-135">The framework layer reads a configuration file and then executes the components specified therein.</span></span> <span data-ttu-id="27f04-136">La couche de composant se compose de trois types de composants : **charger générateurs**, **créateurs de message** et **limiter les contrôleurs**.</span><span class="sxs-lookup"><span data-stu-id="27f04-136">The component layer consists of three types of components: **load generators**, **message creators** and **throttle controllers**.</span></span> <span data-ttu-id="27f04-137">Chacun de ces composants est extensible, afin de pouvoir créer les vôtres et les incorporer LoadGen pour répondre aux besoins de votre scénario.</span><span class="sxs-lookup"><span data-stu-id="27f04-137">Each of these components is extensible, so you can create your own and plug them into LoadGen to address the needs of your scenario.</span></span> <span data-ttu-id="27f04-138">Étant donné que l’outil LoadGen a été développé par le groupe de produits BizTalk Server, vous devez rechercher que les composants out of box effectuera la plupart de vos besoins de test de charge.</span><span class="sxs-lookup"><span data-stu-id="27f04-138">Because LoadGen was developed by the BizTalk Server product group, you should find that the out-of-the-box components will fulfill most of your load testing requirements.</span></span> <span data-ttu-id="27f04-139">Chacun de ces composants est décrite plus en détail ici.</span><span class="sxs-lookup"><span data-stu-id="27f04-139">Each of these components is described in greater detail here.</span></span>  
  
-   <span data-ttu-id="27f04-140">**Charger les générateurs de** est responsable de la transmission des messages via un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="27f04-140">**Load generators** are responsible for transmitting messages via a particular transport.</span></span> <span data-ttu-id="27f04-141">Générateurs de charge sont fournis pour les transports suivants :</span><span class="sxs-lookup"><span data-stu-id="27f04-141">Load generators are provided for the following transports:</span></span>  
  
    -   <span data-ttu-id="27f04-142">Fichier</span><span class="sxs-lookup"><span data-stu-id="27f04-142">File</span></span>  
  
    -   <span data-ttu-id="27f04-143">HTTP</span><span class="sxs-lookup"><span data-stu-id="27f04-143">HTTP</span></span>  
  
    -   <span data-ttu-id="27f04-144">MQSeries</span><span class="sxs-lookup"><span data-stu-id="27f04-144">MQSeries</span></span>  
  
    -   <span data-ttu-id="27f04-145">MSMQLarge</span><span class="sxs-lookup"><span data-stu-id="27f04-145">MSMQLarge</span></span>  
  
    -   <span data-ttu-id="27f04-146">MSMQ</span><span class="sxs-lookup"><span data-stu-id="27f04-146">MSMQ</span></span>  
  
    -   <span data-ttu-id="27f04-147">SOAP</span><span class="sxs-lookup"><span data-stu-id="27f04-147">SOAP</span></span>  
  
    -   <span data-ttu-id="27f04-148">Web Services Enhancements (WSE)</span><span class="sxs-lookup"><span data-stu-id="27f04-148">Web Services Enhancements (WSE)</span></span>  
  
    -   <span data-ttu-id="27f04-149">Windows SharePoint Services (WSS)</span><span class="sxs-lookup"><span data-stu-id="27f04-149">Windows SharePoint Services (WSS)</span></span>  
  
    -   <span data-ttu-id="27f04-150">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="27f04-150">Windows Communication Foundation (WCF)</span></span>  
  
-   <span data-ttu-id="27f04-151">**Créateurs de message** sont un composant facultatif qui peut être utilisé lorsque vous avez besoin générer des messages qui contiennent des données uniques.</span><span class="sxs-lookup"><span data-stu-id="27f04-151">**Message creators** are an optional component that can be used when you need to generate messages that contain unique data.</span></span> <span data-ttu-id="27f04-152">Les créateurs de message utilisent un des deux modes de création ; synchrone et asynchrone.</span><span class="sxs-lookup"><span data-stu-id="27f04-152">Message creators use one of two modes of creation; synchronous and asynchronous.</span></span> <span data-ttu-id="27f04-153">Si le mode de création de messages synchrone est spécifié, LoadGen utilise un seul thread pour créer des messages pour vous assurer que chaque message contienne une charge utile unique.</span><span class="sxs-lookup"><span data-stu-id="27f04-153">If the synchronous message creation mode is specified, LoadGen uses only a single thread to create messages to ensure that each message contains a unique payload.</span></span> <span data-ttu-id="27f04-154">Alors que le mode synchrone garantit des données uniques au sein de chaque message, ce mode limite également l’évolutivité.</span><span class="sxs-lookup"><span data-stu-id="27f04-154">While the synchronous mode guarantees unique data within each message, this mode also limits scalability.</span></span> <span data-ttu-id="27f04-155">LoadGen fournit également aux créateurs de messages asynchrones qui utilisent plusieurs threads d’exécution ; Cela permet de LoadGen répondre à la vitesse de messages cible (car il peut simplement créer plus de threads).</span><span class="sxs-lookup"><span data-stu-id="27f04-155">LoadGen also provides asynchronous message creators that use multiple execution threads; this enables LoadGen to meet the target message rate (because it can simply create more threads).</span></span> <span data-ttu-id="27f04-156">En mode asynchrone, le créateur de message peut être configuré pour modifier les données pour chaque message de façon aléatoire.</span><span class="sxs-lookup"><span data-stu-id="27f04-156">In asynchronous mode, the message creator may be configured to randomly modify data for each individual message.</span></span> <span data-ttu-id="27f04-157">Toutefois, car elle utilise plusieurs threads, il ne garantit pas que tous les messages générés pendant le test contiendra une charge utile unique.</span><span class="sxs-lookup"><span data-stu-id="27f04-157">However, because it uses multiple threads, it does not guarantee that all message generated during the test will contain a unique payload.</span></span>  
  
-   <span data-ttu-id="27f04-158">**Limitation des contrôleurs de** vous assurer que les messages sont transmis à un taux stable en contrôlant les générateurs de charge pendant l’exécution du test.</span><span class="sxs-lookup"><span data-stu-id="27f04-158">**Throttle controllers** ensure that messages are transmitted at a steady rate by governing the load generators while the test is running.</span></span> <span data-ttu-id="27f04-159">LoadGen expose également la limitation personnalisée, qui vous permet de contrôler le flux de messages en fonction de critères, notamment :</span><span class="sxs-lookup"><span data-stu-id="27f04-159">LoadGen also exposes custom throttling, which enables you to control the flow of messages based on criteria including:</span></span>  
  
    -   <span data-ttu-id="27f04-160">Nombre de fichiers dans un dossier</span><span class="sxs-lookup"><span data-stu-id="27f04-160">Number of files in a folder</span></span>  
  
    -   <span data-ttu-id="27f04-161">Nombre de lignes dans une table de base de données</span><span class="sxs-lookup"><span data-stu-id="27f04-161">Number of rows in a database table</span></span>  
  
    -   <span data-ttu-id="27f04-162">Profondeur d’une file d’attente de messages MSMQ ou MQSeries</span><span class="sxs-lookup"><span data-stu-id="27f04-162">Depth of an MSMQ or MQSeries message queue</span></span>  
  
 <span data-ttu-id="27f04-163">Microsoft [outil BizTalk LoadGen 2007](http://go.microsoft.com/fwlink/?LinkId=59841) est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841).</span><span class="sxs-lookup"><span data-stu-id="27f04-163">The Microsoft [BizTalk LoadGen 2007 tool](http://go.microsoft.com/fwlink/?LinkId=59841) is available for download at [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841).</span></span>  
  
### <a name="sample-loadgen-configuration-file"></a><span data-ttu-id="27f04-164">Exemple de fichier de configuration LoadGen</span><span class="sxs-lookup"><span data-stu-id="27f04-164">Sample LoadGen configuration file</span></span>  
 <span data-ttu-id="27f04-165">Toutes les informations de configuration de LoadGen sont stockées dans un fichier xml.</span><span class="sxs-lookup"><span data-stu-id="27f04-165">All LoadGen configuration information is stored in an xml file.</span></span> <span data-ttu-id="27f04-166">Le fichier de configuration LoadGen contient un \<CommonSection > élément qui configure les paramètres par défaut pour toutes les tâches de LoadGen dans le scénario LoadGen.</span><span class="sxs-lookup"><span data-stu-id="27f04-166">The LoadGen configuration file contains a \<CommonSection> element that configures the default settings for all LoadGen tasks in the LoadGen scenario.</span></span> <span data-ttu-id="27f04-167">Le fichier de configuration LoadGen peut également contenir un ou plusieurs \<Section > éléments qui fournissent des paramètres de configuration pour une tâche LoadGen spécifique.</span><span class="sxs-lookup"><span data-stu-id="27f04-167">The LoadGen configuration file can also contain one or more \<Section> elements that provide configuration settings for a specific LoadGen task.</span></span> <span data-ttu-id="27f04-168">Entrées dans un \<Section > élément remplacent les valeurs par défaut spécifiées dans le \<CommonSection > élément.</span><span class="sxs-lookup"><span data-stu-id="27f04-168">Entries in a \<Section> element supersede any default values specified in the \<CommonSection> element.</span></span>  
  
 <span data-ttu-id="27f04-169">L’exemple de fichier de configuration LoadGen qui suit est une version légèrement modifiée du fichier de configuration d’exemple FileToFileLG.xml qui est inclus dans le sous-répertoire \ConfigFiles\ConsoleConfigFiles du répertoire d’installation LoadGen.</span><span class="sxs-lookup"><span data-stu-id="27f04-169">The sample LoadGen configuration file that follows is a slightly modified version of the FileToFileLG.xml sample configuration file that is included in the \ConfigFiles\ConsoleConfigFiles subdirectory of the LoadGen installation directory.</span></span> <span data-ttu-id="27f04-170">Ce test envoie des 25 messages \<LotSizePerInterval > toutes les 200 millisecondes \<SleepInterval >, 5 threads par le Générateur de charge \<NumThreadsperSection > et va s’arrêter le test de charge après les 5000 messages \<%NUMFILES > ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="27f04-170">This test sends 25 messages \<LotSizePerInterval> every 200 milliseconds \<SleepInterval>, 5 threads per load generator \<NumThreadsperSection>and will stop the load test after 5000 messages \<NumFiles> have been sent.</span></span>  
  
 <span data-ttu-id="27f04-171">Le contrôleur de limitation de fichier est spécifié dans le \<ThrottleController > section.</span><span class="sxs-lookup"><span data-stu-id="27f04-171">The file throttle controller is specified in the \<ThrottleController> section.</span></span> <span data-ttu-id="27f04-172">La valeur de \<ThresholdRange > a la valeur 1000 à 2000, ce qui signifie que si l’emplacement du fichier C:\Scenarios\FileToFile\Receive (paramètres) a moins de 1 000 ou plus de 2000 fichiers, le contrôleur de limitation accélèrera le Générateur de fichier et augmenter/diminuer la charge comme il convient.</span><span class="sxs-lookup"><span data-stu-id="27f04-172">The value for \<ThresholdRange> is set to 1000-2000, which means that if the file location C:\Scenarios\FileToFile\Receive (Parameters) has less than 1000 or more than 2000 files, the throttle controller will throttle the file generator and increase/decrease load as appropriate.</span></span> <span data-ttu-id="27f04-173">Le nombre de fichiers dans l’emplacement du fichier sera vérifiée toutes les 1000 millisecondes \<SleepInterval >.</span><span class="sxs-lookup"><span data-stu-id="27f04-173">The number of files in the file location will be checked every 1000 milliseconds \<SleepInterval>.</span></span> <span data-ttu-id="27f04-174">Le \<FileSection > élément définit les propriétés pour les messages envoyés par les générateurs de charge.</span><span class="sxs-lookup"><span data-stu-id="27f04-174">The \<FileSection> element defines the properties for the messages to be sent by the load generators.</span></span> <span data-ttu-id="27f04-175">Le fichier FileToFileLG.xml \<SrcFilePath > LoadGen seront copiés vers le filedrop C:\Scenarios\FileToFile\Receive \<DstFilePath >.</span><span class="sxs-lookup"><span data-stu-id="27f04-175">The FileToFileLG.xml file \<SrcFilePath> will be copied by LoadGen to the filedrop C:\Scenarios\FileToFile\Receive \<DstFilePath>.</span></span> <span data-ttu-id="27f04-176">Le transport de fichier est utilisé ici, car il s’agit du transport par défaut spécifié dans le \<Transport nom > élément dans le \<CommonSection > élément.</span><span class="sxs-lookup"><span data-stu-id="27f04-176">The file transport is used here because this is the default transport specified in the \<Transport Name> element within the \<CommonSection> element.</span></span>  
  
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
  
### <a name="using-bizunit-to-drive-loadgen"></a><span data-ttu-id="27f04-177">À l’aide de BizUnit au lecteur LoadGen</span><span class="sxs-lookup"><span data-stu-id="27f04-177">Using BizUnit to drive LoadGen</span></span>  
 <span data-ttu-id="27f04-178">BizUnit fournit le **LoadGenExecuteStep** pour faciliter automatisée des performances et la stabilité du test.</span><span class="sxs-lookup"><span data-stu-id="27f04-178">BizUnit provides the **LoadGenExecuteStep** to facilitate automated performance and stability testing.</span></span> <span data-ttu-id="27f04-179">Le **TestExecution** étape d’un exemple de fichier de configuration BizUnit qui utilise **LoadGenExecuteStep** est indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="27f04-179">The **TestExecution** stage of a sample BizUnit configuration file that uses **LoadGenExecuteStep** is shown in the following code example.</span></span> <span data-ttu-id="27f04-180">Notez que cette étape accepte un seul paramètre de configuration, qui est l’emplacement du fichier de configuration LoadGen.</span><span class="sxs-lookup"><span data-stu-id="27f04-180">Note that this step accepts a single configuration parameter, which is the location of the LoadGen configuration file.</span></span>  
  
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
  
 <span data-ttu-id="27f04-181">Le reste de cette rubrique décrit le fichier de configuration pour un cas de test BizUnit qui automatise les tests de performances avec l’outil LoadGen.</span><span class="sxs-lookup"><span data-stu-id="27f04-181">The remainder of this topic describes the configuration file for a BizUnit test case that automates performance testing with LoadGen.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27f04-182">Ce fichier de configuration peut être utilisé en tant que modèle à intégrer rapidement BizUnit et LoadGen dans le cadre de vos tests de performances.</span><span class="sxs-lookup"><span data-stu-id="27f04-182">This configuration file can be used as a template to quickly integrate BizUnit and LoadGen as part of your performance testing.</span></span> <span data-ttu-id="27f04-183">Avant d’exécuter ce cas de test, vous devez personnaliser le fichier de configuration pour votre environnement.</span><span class="sxs-lookup"><span data-stu-id="27f04-183">Before running this test case, you will need to customize the configuration file for your environment.</span></span> <span data-ttu-id="27f04-184">Les sections du fichier de configuration qui doivent être personnalisés sont indiquées en conséquence.</span><span class="sxs-lookup"><span data-stu-id="27f04-184">Sections of the configuration file that must be customized are indicated accordingly.</span></span>  
  
 <span data-ttu-id="27f04-185">Pour commencer, spécifiez une valeur pour le **testName** paramètre approprié pour la solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="27f04-185">To begin with, specify a value for the **testName** parameter that is appropriate for the BizTalk solution.</span></span>  
  
```  
<TestCase testName="Performance-Guide-Sample-Loadgen-Test">  
```  
  
 <span data-ttu-id="27f04-186">Puis ajoutez les variables de contexte à la **TestSetup** étape.</span><span class="sxs-lookup"><span data-stu-id="27f04-186">Then add context variables to the **TestSetup** stage.</span></span> <span data-ttu-id="27f04-187">Ces variables de contexte seront référencés dans l’ensemble de la durée du cas de test.</span><span class="sxs-lookup"><span data-stu-id="27f04-187">These context variables will be referenced throughout the duration of the test case.</span></span> <span data-ttu-id="27f04-188">Pour utiliser ce fichier de configuration, modifiez les valeurs spécifiées pour **TestCaseResultsDir** (C:\Dev Work\Perf Guide Demos\PerfResults\\) et **ordinateur** (BIZTALKADMIN01) pour faire correspondre votre environnement.</span><span class="sxs-lookup"><span data-stu-id="27f04-188">To use this configuration file, modify the values specified for **TestCaseResultsDir** (C:\Dev Work\Perf Guide Demos\PerfResults\\) and **Machine** (BIZTALKADMIN01) to match your environment.</span></span>  
  
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
  
 <span data-ttu-id="27f04-189">Après avoir effectué la **TestSetup** étape, nous permet d’entrer le **TestExecution** étape.</span><span class="sxs-lookup"><span data-stu-id="27f04-189">After completing the **TestSetup** stage, we enter the **TestExecution** stage.</span></span> <span data-ttu-id="27f04-190">La première étape consiste à arrêter les instances d’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="27f04-190">The first step is to stop the BizTalk host instances.</span></span> <span data-ttu-id="27f04-191">Distinct **BizUnit.HostConductorStep** section doit être ajoutée pour chaque instance d’hôte distinctes.</span><span class="sxs-lookup"><span data-stu-id="27f04-191">A separate **BizUnit.HostConductorStep** section must be added for each distinct host instance.</span></span> <span data-ttu-id="27f04-192">Si vous utilisez ce fichier de configuration dans votre environnement, vous devez également entrer les valeurs appropriées pour **HostInstanceName**, **Server**, **ouverture de session**et  **Mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="27f04-192">If you are using this configuration file in your environment, you will also need to enter the appropriate values for **HostInstanceName**, **Server**, **Logon**, and **Password**.</span></span>  
  
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
  
 <span data-ttu-id="27f04-193">Après l’arrêt de toutes les instances d’hôte, nous nettoyer la base de données BizTalk MessageBox à l’aide de la bts_CleanupMsgBox procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="27f04-193">After stopping all of the host instances, we clean up the BizTalk MessageBox database using the bts_CleanupMsgBox stored procedure.</span></span> <span data-ttu-id="27f04-194">Pour utiliser cette étape, vous devez modifier la valeur de **ConnectionString** pour correspondre à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="27f04-194">To use this step you must modify the value for **ConnectionString** to match your environment.</span></span>  
  
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
  
 <span data-ttu-id="27f04-195">Étape 3 de la **TestExecution** étape démarre les compteurs de l’Analyseur de performances (PerfMon) qui sont spécifiés dans un fichier de modèle.</span><span class="sxs-lookup"><span data-stu-id="27f04-195">Step 3 of the **TestExecution** stage starts Performance Monitor (PerfMon) counters that are specified in a template file.</span></span> <span data-ttu-id="27f04-196">Un exemple de fichier de modèle est répertorié sous l’exemple **BizUnit.PerfmonCountersStep** ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="27f04-196">A sample template file is listed underneath the sample **BizUnit.PerfmonCountersStep** below.</span></span> <span data-ttu-id="27f04-197">Pour utiliser le fichier de modèle, vous devez modifier la valeur spécifiée pour **CountersListFilePath** à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="27f04-197">To use the template file, you must modify the value specified for **CountersListFilePath** to match your environment.</span></span> <span data-ttu-id="27f04-198">Modifier le fichier de modèle du compteur exemple performances moniteur pour inclure des compteurs PerfMon que vous souhaitez analyser ou supprimez ceux qui ne sont pas pertinentes pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="27f04-198">Modify the sample performance monitor counter template file to include any PerfMon counters that you would like to monitor or remove any that are not relevant to your scenario.</span></span>  
  
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
  
 <span data-ttu-id="27f04-199">**Fichier modèle de compteur d’analyseur de performances exemple (Test_06_PerfCounters.txt référencé par le BizUnit.PerfmonCountersStep) :**</span><span class="sxs-lookup"><span data-stu-id="27f04-199">**Sample Performance Monitor counter template file (Test_06_PerfCounters.txt referenced by the BizUnit.PerfmonCountersStep):**</span></span>  
  
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
  
 <span data-ttu-id="27f04-200">Maintenant, nous allons commencer les instances d’hôte BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="27f04-200">Now we start the BizTalk Server host instances.</span></span> <span data-ttu-id="27f04-201">Distinct **BizUnit.HostConductorStep** section doit être ajoutée pour chaque instance d’hôte distinctes (distinct inclut plusieurs instances d’un ordinateur hôte sur les serveurs).</span><span class="sxs-lookup"><span data-stu-id="27f04-201">A separate **BizUnit.HostConductorStep** section must be added for each distinct host instance (distinct includes multiple instances of a host across servers).</span></span> <span data-ttu-id="27f04-202">Si vous utilisez ce fichier de configuration dans votre environnement, vous devez également entrer les valeurs appropriées pour **HostInstanceName**, **Server**, **ouverture de session**et  **Mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="27f04-202">If you are using this configuration file in your environment, you will also need to enter the appropriate values for **HostInstanceName**, **Server**, **Logon**, and **Password**.</span></span>  
  
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
  
 <span data-ttu-id="27f04-203">Étape 5 » primes « le système en envoyant des deux messages à l’aide de BizTalk Server **BizUnit.LoadGenExecuteStep**; modifier la valeur de la **LoadGenTestConfig** paramètre à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="27f04-203">Step 5 “primes” the system by sending a couple of messages to BizTalk Server using **BizUnit.LoadGenExecuteStep**; change the value of the **LoadGenTestConfig** parameter to match your environment.</span></span>  
  
```  
<!-- Step 5: Send Priming messages -->  
<TestStep assemblyPath="" typeName="BizUnit.LoadGenExecuteStep, BizUnit.LoadGenSteps">  
   <LoadGenTestConfig>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</LoadGenTestConfig>  
</TestStep>  
```  
  
 <span data-ttu-id="27f04-204">Étape 6 a écrit le fichier de configuration LoadGen dans la mémoire afin qu’il peut ensuite être écrit à la base de données des résultats de test lorsque le test est terminé.</span><span class="sxs-lookup"><span data-stu-id="27f04-204">Step 6 writes the LoadGen configuration file to memory so that it can then be written to the test results database when the test is complete.</span></span>  
  
```  
  
      <!-- Step 6: Read loadgen file into context variable -->  
<TestStep assemblyPath="" typeName="BizUnit.FileReadAndLoadToContext">  
   <FilePath>C:\Program Files\LoadGen\ConfigFiles\ConsoleConfigFiles\PerfGuideFiletoFile.xml</FilePath>  
   <ContextPropertyName>LoadGenFileContent</ContextPropertyName>  
</TestStep>  
```  
  
 <span data-ttu-id="27f04-205">Maintenant, nous écrivons l’heure de début de test à une base de données des résultats de test.</span><span class="sxs-lookup"><span data-stu-id="27f04-205">Now we write the test start time to a test results database.</span></span> <span data-ttu-id="27f04-206">Modifier la **ConnectionString** et **RawSQLQuery** paramètres devant correspondre à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="27f04-206">Modify the **ConnectionString** and **RawSQLQuery** parameters to match your environment.</span></span>  
  
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
  
 <span data-ttu-id="27f04-207">Étape 8 est où le test de performances réel est lancée à l’aide de **BizUnit.LoadGenExecuteStep**.</span><span class="sxs-lookup"><span data-stu-id="27f04-207">Step 8 is where the actual performance test is initiated using **BizUnit.LoadGenExecuteStep**.</span></span> <span data-ttu-id="27f04-208">Cette étape spécifie le même fichier de configuration LoadGen a été utilisé à l’étape 5, mais vous pouvez spécifier n’importe quel fichier de configuration LoadGen valide ici.</span><span class="sxs-lookup"><span data-stu-id="27f04-208">This step specifies the same LoadGen configuration file that was used in step 5, but you can specify any valid LoadGen configuration file here.</span></span> <span data-ttu-id="27f04-209">**BizUnit.DelayStep** est utilisé à l’étape 9 pour imposer un délai de 5 secondes pour laisser le temps pour les messages à circuler via le système.</span><span class="sxs-lookup"><span data-stu-id="27f04-209">**BizUnit.DelayStep** is used in step 9 to impose a 5-second delay to allow time for messages to start flowing through the system.</span></span> <span data-ttu-id="27f04-210">Longueur de file d’attente hôte est calculée à l’aide de **BizUnit.PerMonCounterMonitorStep**.</span><span class="sxs-lookup"><span data-stu-id="27f04-210">Host queue length is calculated using **BizUnit.PerMonCounterMonitorStep**.</span></span> <span data-ttu-id="27f04-211">Lorsque ce paramètre atteint la valeur 1 comme indiqué dans l’étape 10, le test est terminé.</span><span class="sxs-lookup"><span data-stu-id="27f04-211">When this parameter reaches a value of 1 as specified in step 10, the test is concluded.</span></span> <span data-ttu-id="27f04-212">Modifier les valeurs pour le **InstanceName** et **Server** paramètres correspondre au nom de l’instance de l’hôte et le serveur que vous souhaitez surveiller dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="27f04-212">Change the values for the **InstanceName** and **Server** parameters to match the name of the host instance and server that you would like to monitor in your environment.</span></span>  
  
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
  
 <span data-ttu-id="27f04-213">À la fin du test, nous utilisons **BizUnit.DBExecuteNonQueryStep** pour mettre à jour la base de données des résultats de test.</span><span class="sxs-lookup"><span data-stu-id="27f04-213">At the conclusion of the test we use **BizUnit.DBExecuteNonQueryStep** to update the test results database.</span></span> <span data-ttu-id="27f04-214">Issue de cette étape correspond à la fin de l’étape d’exécution du test, comme indiqué par la fermeture \</TestExecution > balise.</span><span class="sxs-lookup"><span data-stu-id="27f04-214">Completion of this step signifies the end of the test execution stage, as indicated by the closing \</TestExecution> tag.</span></span> <span data-ttu-id="27f04-215">Là encore, vous devez modifier le **ConnectionString** et **RawSQLQuery** paramètres devant correspondre à votre environnement.</span><span class="sxs-lookup"><span data-stu-id="27f04-215">Again, you must modify the **ConnectionString** and **RawSQLQuery** parameters to match your environment.</span></span>  
  
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
  
 <span data-ttu-id="27f04-216">Entrez l’étape de nettoyage de test lors de la conclusion de l’étape d’exécution.</span><span class="sxs-lookup"><span data-stu-id="27f04-216">Upon concluding the execution stage we enter the test cleanup stage.</span></span> <span data-ttu-id="27f04-217">Cette étape utilise **BizUnit.PerfmonCountersStep** pour désactiver les compteurs de l’Analyseur de performances qui ont été démarrées précédemment (à l’étape 3).</span><span class="sxs-lookup"><span data-stu-id="27f04-217">This stage uses **BizUnit.PerfmonCountersStep** to stop the Performance Monitor counters that were started earlier (in Step 3).</span></span>  
  
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
  
 <span data-ttu-id="27f04-218">Cet exemple illustre comment BizUnit peut être combinée avec l’outil LoadGen pour automatiser le test de performances.</span><span class="sxs-lookup"><span data-stu-id="27f04-218">This example illustrated how BizUnit can be combined with LoadGen to automate performance testing.</span></span> <span data-ttu-id="27f04-219">Le test de charge décrit par le fichier de configuration BizUnit peut être exécuté à partir des outils de test de Visual Studio, dans la même manière que les tests fonctionnels.</span><span class="sxs-lookup"><span data-stu-id="27f04-219">The load test described by the BizUnit configuration file can be executed from Visual Studio’s testing tools in the same manner as the functional testing.</span></span> <span data-ttu-id="27f04-220">Adoptant cette approche vous permet de gérer, administrer et collecter des données pour vos tests de performances de manière centralisée.</span><span class="sxs-lookup"><span data-stu-id="27f04-220">Adopting this approach enables you to centrally manage, administer, and collect data for your performance testing.</span></span>  
  
 <span data-ttu-id="27f04-221">À l’aide de BizUnit et LoadGen dans une approche automatisée, il est très facile à planifier plusieurs séries de tests qui se produirait hors des heures, ce qui fournissent des résultats des tests suffisamment pour l’analyse pendant les heures de travail normales.</span><span class="sxs-lookup"><span data-stu-id="27f04-221">By using BizUnit and LoadGen in an automated approach, it is very easy to schedule multiple test runs to occur during off hours, which will provide ample test results for analysis during normal working hours.</span></span> <span data-ttu-id="27f04-222">Lors de l’automatisation des tests de performances, envisagez d’utiliser des scripts de LoadGen que modèle différentes charges par le système, par exemple vous pouvez souhaiter simuler des degrés divers (75 % et 100 % de 125 %) du volume de message de production prévu.</span><span class="sxs-lookup"><span data-stu-id="27f04-222">When automating performance testing, consider using LoadGen scripts that model different loads through the system, for example you may wish to simulate varying degrees (75%, 100% and 125%) of the expected production message volume.</span></span> <span data-ttu-id="27f04-223">Lorsque vous effectuez le test de charge, il est particulièrement important de tester la surcharge ou le scénario de « journée incorrect ».</span><span class="sxs-lookup"><span data-stu-id="27f04-223">When performing load testing, it is especially important to test the overload or “bad day” scenario.</span></span> <span data-ttu-id="27f04-224">Avant de placer le système en production, vous devez savoir quel est le débit maximal acceptable (MST) pour chaque cas de test dans l’environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="27f04-224">Before placing the system into production, you should know what the maximum sustainable throughput (MST) is for each test case in the BizTalk Server environment.</span></span> <span data-ttu-id="27f04-225">Pour plus d’informations sur les performances maximales admissibles, consultez [Nouveautés des performances durables ?](http://go.microsoft.com/fwlink/?LinkID=132304)</span><span class="sxs-lookup"><span data-stu-id="27f04-225">For more information about maximum sustainable performance, see [What Is Sustainable Performance?](http://go.microsoft.com/fwlink/?LinkID=132304)</span></span> <span data-ttu-id="27f04-226">(http://go.microsoft.com/fwlink/?LinkID=132304) dans la documentation de BizTalk Server 2009.</span><span class="sxs-lookup"><span data-stu-id="27f04-226">(http://go.microsoft.com/fwlink/?LinkID=132304) in the BizTalk Server 2009 documentation.</span></span>  
  
### <a name="the-complete-bizunit-loadgen-sample-configuration-file"></a><span data-ttu-id="27f04-227">Le fichier de configuration d’exemple BizUnit LoadGen terminé</span><span class="sxs-lookup"><span data-stu-id="27f04-227">The complete BizUnit LoadGen sample configuration file</span></span>  
 <span data-ttu-id="27f04-228">La liste suivante contient tout le contenu du fichier de configuration BizUnit mentionnés précédemment.</span><span class="sxs-lookup"><span data-stu-id="27f04-228">The following list contains the entire contents of the BizUnit configuration file referenced earlier.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27f04-229">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27f04-229">See Also</span></span>  
 [<span data-ttu-id="27f04-230">Pour faciliter les tests automatisés à l’aide de BizUnit</span><span class="sxs-lookup"><span data-stu-id="27f04-230">Using BizUnit to Facilitate Automated Testing</span></span>](../technical-guides/using-bizunit-to-facilitate-automated-testing.md)