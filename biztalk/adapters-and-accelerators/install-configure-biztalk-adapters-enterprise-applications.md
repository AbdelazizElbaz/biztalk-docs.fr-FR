---
title: Installer des adaptateurs BizTalk pour les Applications d’entreprise | Documents Microsoft
description: Configuration requise et les étapes d’installation sur le serveur BizTalk pour JD Edwards OneWorld, JD Edwards EnterpriseOne, PeopleSoft Enterprise, TIBCO Rendezvous et TIBCO Enterprise Message Service
ms.custom: ''
ms.date: 10/13/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa1a09f3d9fa531cee51ecd0e94b99ab972ba13
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="install-and-configure-the-microsoft-biztalk-adapters-for-enterprise-applications"></a>Installer et configurer les adaptateurs Microsoft BizTalk pour les Applications d’entreprise 
  
 Adaptateurs Microsoft BizTalk pour les Applications d’entreprise inclut les adaptateurs suivants :  
  
-   Adaptateur Microsoft BizTalk pour JD Edwards OneWorld  
  
-   Adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne  
  
-   Adaptateur Microsoft BizTalk pour PeopleSoft Enterprise  
  
-   Adaptateur Microsoft BizTalk pour TIBCO Rendezvous  
  
-   Adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service  


> [!IMPORTANT]
> - Sauvegardez toutes les données avant d’apporter des modifications de configuration
> - Vous devez être familiarisé avec l’application d’entreprise spécifique avant d’apporter des modifications de configuration
  
## <a name="supported-versions--requirements"></a>Configuration requise et les versions prises en charge

||Spécifications|  
|---|---|
|Système d'exploitation|L’adaptateur prend en charge le même système d’exploitation que BizTalk Server :<ul><li>[Configuration requise de BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)</li><li>[BizTalk Server 2013 R2 / 2013 configuration requise](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)</li></ul>|
|Système d’entreprise pris en charge|[Prise en charge des systèmes d’entreprise et de métier (LOB)](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) répertorie les versions prises en charge |
|JD Edwards OneWorld XE | <ul><li>Serveur JD Edwards Enterprise sur Windows</li><li>Serveur de déploiement JD Edwards sur Windows</li></ul>|
|JD Edwards EnterpriseOne | L’adaptateur appelle l’API JD Edwards EnterpriseOne qui utilise JDBC, lequel a besoin d’un pilote pour la base de données. Si vous installez JD Edwards EnterpriseOne avec une base de données SQL, vous avez besoin de pilotes MS-SQL. Même si vous avez installé JD Edwards EnterpriseOne avec une base de données Oracle, vous avez besoin de pilotes Oracle ; ou, si vous avez installé une base de données DB2, vous avez besoin de pilotes de DB2. |
|PeopleSoft Enterprise | <ul><li>Sun Systems Java Development Kit (JDK)</li><li>Version des outils PeopleSoft</li><li>Publication d’Applications PeopleSoft</li><li>Cet adaptateur requiert une modification de l’application PeopleSoft. Pour utiliser les interfaces de composant, téléchargez une interface de composant personnalisée, GET_CI_INFO, dans PeopleSoft. GET_CI_INFO.PC concerne dans Program Files\Common Files\Microsoft BizTalk Adapters Enterprise \Config\.</li></ul>|
|TIBCO Rendezvous | <ul><li>Le composant d’exécution TIBCO Rendezvous doit être installé sur l’ordinateur sur lequel s’exécute l’adaptateur BizTalk pour TIBCO Rendezvous</li><li>La licence de TIBCO Rendezvous doit être configurée sur l’ordinateur sur lequel s’exécute l’adaptateur BizTalk pour TIBCO Rendezvous.</li><li>Le répertoire des fichiers binaires TIBCO Rendezvous doit être visible par l'adaptateur : soit dans la valeur PATH des variables d'environnement, soit spécifié sur chaque port Rendezvous dans BizTalk Server. Cela est nécessaire pour que l'assembly Rendezvous trouve ses bibliothèques et son exécutable.</li></ul>|
|TIBCO Enterprise Message Service | Version de Enterprise Message Service (EMS) 5.x et versions ultérieures inclut un client SDK (à l’aide de l’API TIBCO EMS c#). L’adaptateur BizTalk pour TIBCO EMS utilise pour communiquer avec le serveur. |


## <a name="jd-edwards-oneworld-xe"></a>JD Edwards OneWorld XE

Cette section comprend des informations essentielles sur l’utilisation de l’adaptateur Microsoft BizTalk pour JD Edwards OneWorld XE avec BizTalk Server.
  
### <a name="create-the-jar-files"></a>Créer les fichiers JAR
 Cette section décrit la configuration requise pour que JD Edwards OneWorld fonctionne avec l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld.  
  
#### <a name="jar-files-and-the-classpath"></a>Fichiers JAR et CLASSPATH  
 Fichiers JAR JD Edwards OneWorld doivent être disponibles à l’adaptateur. Par exemple, pour vous connecter à la Version B7.3.3.3, les fichiers jar suivants sont requis. En fonction du serveur que vous vous connectez, la liste des fichiers jar peut changer :
  
-   Connector.jar    
-   Kernel.jar  
  
 Ces fichiers se trouvent sur un ordinateur exécutant JD Edwards OneWorld, aux emplacements suivants :  
  
-   Répertoire_installation_JD_Edwards_OneWorld_XE\System\classes\Connector.jar    
-   JD Edwards OneWorld XE_install_Directory\System\classes\Kernel.jar  
  
 Vous pouvez copier ces fichiers vers l'emplacement de votre choix. Vous devez toutefois spécifier l'emplacement des fichiers JAR dans CLASSPATH. CLASSPATH doit inclure à la fois le chemin d'accès complet et le nom du fichier JAR (séparés par un point-virgule).  
  
 L’adaptateur BizTalk pour JD Edwards OneWorld fournit le fichier JAR de JDEJAccess pour une utilisation avec JD Edwards OneWorld. Par défaut, le fichier JDEJAccess.jar est référencé à partir *Program Files\Common Files\Microsoft BizTalk Adapters pour applications\j.d d’entreprise. Edwards OneWorld(r)\classes\JDEJAccess.jar*. 
  
> [!NOTE]
>  Vous devez vérifier l'inscription du fichier jdeinterop.ini avant de pouvoir utiliser l'adaptateur BizTalk pour JD Edwards OneWorld. Assurez-vous que vous incluez un chemin d’accès à ce fichier dans le **propriété du Transport JDE** page lorsque vous créez le port d’envoi dans BizTalk Server. Pour obtenir une explication complète, consultez « Personnalisation du fichier jdeinterop.ini ».  
  
#### <a name="create-the-btslibinteropjar-file"></a>Créer le fichier BTSLIBinterop.jar  
Créer le fichier et confirmez qu’il est accessible par l’adaptateur. Utilisez l’exemple suivant comme guide :  
  
1.  Créez le fichier BTSLIB.cmd qui contient le code suivant :  
  
    ```  
    define library BTSLIB  
    login  
    library BTSLIB  
    interface JDEAdapter  
    import B5500900  
    build  
    logout  
    ```  
  
2.  Exécutez la commande suivante :  
  
    ```  
    GenJava  /cmd  .\BTSLIB.cmd  
    ```  
  
### <a name="verify-your-setup"></a>Vérifiez votre configuration  
  
1.  Utiliser une version prise en charge, y compris le numéro de service pack ([prises en charge de métier (LOB) et les systèmes d’entreprise](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)). Les Service Packs (ESU et ASU) mettent à jour les fichiers binaires système. Le Pack Service requis propose une option de menu ASU/ESU pour l'importation.  
  
2.  Configurer le fichier jdeinterop.ini pour utiliser le lecteur approprié pour la journalisation, s’il diffère de lecteur C. Par exemple, votre mise à jour de JD Edwards OneWorld peut échouer si le répertoire TEMP est saturé.  
  
3.  Déterminez si vous devez ajouter un fichier de configuration pour la marge intérieure gauche/droite des champs JD Edwards OneWorld.  
  
4.  Vérifiez que votre variable d'environnement JAVA_HOME pointe vers votre installation du Kit de développement Java (JDK) pour activer les commandes javac et java à partir de n'importe quel programme sur l'ordinateur.  
  
5.  Vérifiez que la variable d’environnement CLASSPATH est définie. Ainsi, l’adaptateur BizTalk pour JD Edwards OneWorld localiser les fichiers Kernel.jar et Connect.jar.  
  
    Le chemin d'accès des fichiers JAR respecte la casse.  
  
6.  Testez l'environnement en tapant la commande suivante, qui respecte la casse.  
  
    ```  
    javap -s -p com.microsoft.jde.JDEJAccess  
    ```  
  
7.  La commande que vous donnez, javap, est le désassembleur de fichier de classe Java :  
  
    ```  
    http://java.sun.com/j2se/1.3/docs/tooldocs/solaris/javap.html  
    ```  
  
8.  Le `javap` commande désassemble un fichier de classe. Sa sortie varie en fonction des options utilisées. Si aucune option n’est utilisée, javap imprime le package, protégé et les champs publics et les méthodes des classes qui lui est passés. javap affiche sa sortie dans stdout.  
  
     S'il n'y a pas d'erreurs, tous les fichiers Java et leurs dépendances se trouvent dans CLASSPATH.  
  
9. Définir la résolution DNS en configurant le fichier d’hôte local (*C:\WINNT\system32\drivers\etc\hosts*), avec le nom du serveur du système JD Edwards OneWorld.  
  
### <a name="create-and-install-the-custom-package"></a>Créez et installez le package personnalisé  
Installez le package personnalisé BTSREL pour utiliser l’adaptateur BizTalk pour JD Edwards OneWorld. Cette section décrit :  
  
-   Le processus de création de package personnalisé JD Edwards OneWorld  
-   La création et l’installation de BTSREL  
-   Les objets BTSREL créés dans JD Edwards OneWorld
  
> [!NOTE]
>  BTSREL.exe est un package personnalisé, ou ASU (Automated Software Update, mise à jour logicielle automatisée) dans la terminologie JD Edwards OneWorld. Il contient des fonctions commerciales permettant d'extraire des métadonnées. Un package personnalisé doit être créé pour une configuration et une version spécifiques de JD Edwards OneWorld.  
  
#### <a name="define-a-custom-package"></a>Définir un package personnalisé  
 Un package personnalisé est un livrable après sortie commerciale qui fournit des modifications logicielles à des fins spécifiques, telles que des modifications de réglementation ou des améliorations. Ces packages personnalisés sont créés pour des fonctionnalités spécifiques. Par exemple, BTSREL est créé pour extraire des métadonnées. Lorsque le package personnalisé BTSREL est installé, il met à jour les modules sélectionnés dans l'environnement JD Edwards OneWorld. Pour être mis à jour, les objets BTSREL doivent être fusionnés dans l'environnement JD Edwards OneWorld approprié. Pour obtenir une liste détaillée des modules mis à jour par BTSREL, consultez la liste des modules.  
  
#### <a name="install-the-btsrel-custom-package"></a>Installer le package personnalisé BTSREL   
Télécharger [BTSREL](https://www.microsoft.com/download/details.aspx?id=56113). Installer sur le serveur de déploiement, puis déployez-le sur le serveur d’entreprise.  
  
 Le package BTSREL.exe existant fonctionne directement avec la version B7333. Pour le package fonctionne avec la version B7334, puis :  
  
1.  Téléchargez et extrayez le contenu de BTSREL.exe dans votre dossier de travail.  
  
2.  Modifiez les deux le **ReleaseLevelRequired** et **version** valeurs b7334 dans le fichier Deployment.Inf.  
  
3.  Exécutez le programme d’installation.  
  
 Pour installer BTSREL, les conditions suivantes sont requises :  
  
-   Installation du serveur de déploiement    
-   Banc d'essai de l'installation  
  
#### <a name="install-btsrel-on-the-deployment-server"></a>Installation de BTSREL sur le serveur de déploiement  
 Personnalisé package fonctionne uniquement sur un système d’exploitation Windows et est utilisé avec le serveur de déploiement. Il doit être créé sur le serveur de déploiement et puis déployé sur le serveur d’entreprise. Le serveur d'entreprise est généralement un serveur de production. Par ailleurs, il peut se trouver sur un système d'exploitation Windows ou UNIX.  
  
> [!NOTE]
>  Lorsque vous appliquez l’ASU au serveur de déploiement JD Edwards OneWorld, vérifiez que vous êtes en **mise à jour** mode. Le **preuve** mode vérifie qu’il n’y a pas de bogues dans l’ASU, tandis que **mise à jour** mode est désigné pour lorsque vous appliquez l’ASU.  
  
1.  Connectez-vous au serveur de déploiement en tant qu’utilisateur **JDE**.  
  
2.  Créez un dossier nommé BTSREL sur le dossier (racine)/B7 du serveur de déploiement.  
  
3.  Copiez BTSREL.exe vers le dossier BTSREL nouvellement créé.  
  
4.  Exécutez BTSREL.exe à partir du dossier .../B7/BTSREL. Le Gestionnaire d’installation démarre automatiquement.  
  
5.  Dans la fenêtre d’installation, sélectionnez **suivant**, puis sélectionnez **Terminer**. Un message s’affiche si l’installation a réussi.  
  
6.  Se connecter à l’environnement JDEPLAN en tant que le**JDE** utilisateur sur le serveur de déploiement JD Edwards OneWorld.  
  
    1.  Si la mise à jour logicielle électronique (ESU) qui inclut le SAR #4533357 n’est pas installé sur le système, sélectionnez **mises à jour logicielles** à partir de la **outils d’Installation de système** menu (GH9612).  
  
    2.  Entrez 02 pour l’option 1 dans le **les Options de traitement** Panneau de configuration.  
  
    3.  Si le ESU qui inclut le SAR #4533357 a été installé sur le système, sélectionnez **Application mise à jour** à partir de la **outils d’Installation de système** menu (GH9612).  
  
#### <a name="install-btsrel-on-the-jd-edwards-oneworld-workbench"></a>Installation de BTSREL sur le banc d’essai JD Edwards OneWorld  
   
1.  Sur le **fonctionne avec la mise à jour de l’Application** écran, double-cliquez sur la mise à jour BTSREL, puis sélectionnez **suivant**.  
  
2.  Double-cliquez sur les environnements où la mise à jour installée, puis **suivant**.  
  
    1.  Vérifiez **banc d’essai sans assistance** si vous souhaitez que la mise à jour de logiciel à s’exécuter en mode sans assistance.  
  
    2.  Sélectionnez **sauvegarde** si vous souhaitez que la sauvegarde des spécifications (de sorte que les spécifications d’origine peuvent être restaurées).  
  
3.  Sur le **fonctionne avec le Plan d’Installation** écran, sélectionnez le plan pour la mise à jour que vous installez, puis **sélectionnez**.  
  
4.  Une fois l'installation terminée, recherchez les erreurs dans les documents PDF générés automatiquement.  
  
    > [!NOTE]
    >  Si des erreurs se produisent, recherchez des conseils de résolution des problèmes dans le Guide des mises à jour logicielles de JD Edwards OneWorld, ou contactez directement JD Edwards OneWorld.  
  
5.  Inscrire manuellement la bibliothèque de fonctions d’entreprise à l’aide de la procédure figurant dans « Inscrire manuellement la bibliothèque de fonctions commerciales » dans cette section.  
  
#### <a name="uninstall-the-custom-package"></a>Désinstaller le package personnalisé  
 Il n'est pas nécessaire de désinstaller le package personnalisé. Toutefois, si vous souhaitez nettoyer le système, vous pouvez le désinstaller de différentes façons. Après avoir désinstallé, régénérez le package à l’aide d’une des méthodes suivantes :  
  
-   Utiliser le serveur de déploiement de JD Edwards OneWorld, Gh8612, P96470, dans le **ligne** menu, sélectionnez **mise à jour**, puis sélectionnez **désinstallation**.    
-   Extrayez tous les objets personnalisés (BTSREL) sur un ordinateur client, puis supprimez-les.    
-   Appliquez un précédent instantané de la base de données.  
  
 Pendant le nettoyage, vérifiez toutes les autres modifications apportées aux autres objets de JD Edwards OneWorld.  
  
#### <a name="manually-register-the-business-function-library"></a>Inscrire manuellement la bibliothèque de fonctions commerciales  
 En raison d'une limitation du processus d'empaquetage du produit JD Edwards OneWorld, la DLL de la bibliothèque de fonctions commerciales personnalisée pour l'adaptateur BizTalk pour JD Edwards OneWorld doit être inscrite manuellement auprès de JD Edwards OneWorld. Ce processus se compose des étapes suivantes.
  
##### <a name="step-1-create-the-custom-business-function-library"></a>Étape 1 : Créer la bibliothèque de fonctions métier personnalisée  
 À l'aide de JD Edwards OneWorld Object Management Workbench (OMW), créez la bibliothèque de fonctions commerciales personnalisée. La procédure suivante doit être effectuée sur l’installation initiale et s’applique à toutes les plateformes.  
  
1.  Démarrer Object Management Workbench (chemin d’accès rapide : « OMW » ou menu Sélection : GH902 objet : P98220).  
  
2.  Sélectionnez **ajouter**, puis sélectionnez l’option pour **bibliothèque de fonctions commerciales**.  
  
3.  Entrez les informations suivantes pour le nouvel objet de bibliothèque de fonctions commerciales :  
  
    -   **Nom :** ACBLIB    
    -   **Description :** DLL Microsoft    
    -   **Code de produit :** 55    
    -   **Code de produit système :** 55  
  
4.  Sélectionnez **OK**.  
  
##### <a name="step-2-rebuild-libraries-from-the-deployment-server"></a>Étape 2 : Régénérez les bibliothèques à partir du serveur de déploiement  
Effectuez les étapes suivantes sur l’installation initiale pour chaque plateforme.  
  
1.  Pour démarrer le programme BusBuild en mode autonome, sélectionnez **Démarrer**, sélectionnez **exécuter**, puis sélectionnez **busbuild.exe**.
  
2.  Connectez-vous à JD Edwards OneWorld dans le pathcode (PY7333, PD7333 ou DV7333).  
  
3.  Dans le **régénérer les bibliothèques** liste, sélectionnez le **Build**.  
  
##### <a name="step-3-copy-the-custom-dll"></a>Étape 3 : Copier la DLL personnalisée  
 Copiez la DLL personnalisée à partir du répertoire de pathcode vers les répertoires de package parent sur le serveur de déploiement JD Edwards OneWorld et sur le serveur d’entreprise JD Edwards OneWorld.
  
**Sur le serveur de déploiement JD Edwards OneWorld XE**  
  
1.  Copiez ACBLIB.dll de DV7333\bin32 vers DV7333\Packages\DV7333FA\bin32.  
  
2.  Copiez ACBLIB.def, ACBLIB.dmp et ACBLIB.mak du dossier DV7333\obj vers le dossier DV7333\Packages\DV7333FA\obj.  
  
3.  Copiez ACBLIB.exp, ACBLIB.lib et sACBLIB.lib à partir du dossier DV7333\lib32 DV7333\Packages\DV7333FA\lib32 dossier.  
  
**Sur le serveur d’entreprise de OneWorld de JD Edwards**  
  
Une fois chaque répertoire et fichier créé, vérifiez l'autorisation.  
  
1.  Créez un répertoire ACBLIB sous DV7333FA\obj\\.  
  
2.  Créez un répertoire ACBLIB sous DV7333FA\source.  
  
3.  FTP b5500900.c du répertoire DV7333\source du serveur de déploiement vers le répertoire DV7333FA\source\ACBLIB.  
  
4.  B5500900.h FTP à partir du répertoire de déploiement serveur DV7333\include DV7333FA\include répertoire.  
  
##### <a name="step-4-build-a-full-package"></a>Étape 4 : Créer un Package complet  
 En raison d’une limitation du processus de génération de package JD Edwards, créer un package complet pour les environnements auxquels vous avez appliqué la mise à jour BTSREL, ou la génération de package de mise à jour ne fonctionne pas correctement. Consultez la documentation de JD Edwards relative à la génération d'un package complet.  
  
> [!NOTE]
>  Lorsque vous appliquez les mises à jour ASU/ESU JD Edwards OneWorld, elles ne créent généralement pas de nouvelles bibliothèques et les fonctions commerciales. Par conséquent, le processus est simple : Toutefois, l’adaptateur BizTalk pour le package personnalisé de JD Edwards OneWorld crée une nouvelle bibliothèque. Par conséquent, vous devez effectuer des étapes supplémentaires, telles que manuellement de créer un répertoire et exécutez une build de package complet.  
  
#### <a name="modules-list"></a>Liste des modules  
 Le package personnalisé BTSREL crée les objets suivants dans JD Edwards OneWorld. BTSREL contient des fonctions commerciales permettant d'extraire les métadonnées et les fonctions personnalisées pour tester les types de données.  
  
> [!NOTE]
>  Il existe un bogue dans la mise à jour de JD Edwards OneWorld. Si vous n’avez pas toutes les fonctions commerciales et personnalisées, vérifiez qu’une génération de package complet a été exécutée, au lieu d’une génération de package de mise à jour.  
>  
>  S'il manque des fichiers dans la liste, par exemple si vous avez tout ce qui figure sous ACBTEST mais rien de ce qui figure au-dessus, il vous manque peut-être les éléments de dictionnaire de données (DD). Vous pouvez accéder à **des éléments de travail avec des données** et recherchez les fichiers manquants.  
>   
>  Si vous ne disposez pas des autres éléments, tels que qu’ACBCHAR01, ACBDATE01, ADBINT01, ACBMATH01 et ACBSTR01, il s’agit du *des éléments de données principal*. Lorsque vous fusionnez des objets du planificateur vers le développement (DEV), de nombreux rapports s'exécutent en arrière-plan. Vous pouvez ouvrir les rapports de fusion et recherchez les éventuelles erreurs. Les rapports doivent répertorier tous les éléments et indiquer qu'elles ont été accomplies sans erreur ou avertissement. Avec cette vérification, vous pouvez continuer, car tous les éléments sont comptabilisés.  
  
-   ACBCHAR01 - TEST CHAR TYPE 01  
  
-   ACBCUST - ACB CUSTOMER ID  
  
-   ACBDATE01 - TYPE DE DATE TEST 01  
  
-   ACBDEF - ACB FUNCTION TYPE DEFINITION  
  
-   ACBFCNT - ACB FUNCTION NAME LIST COUNT  
  
-   ACBFUNC - LISTE DES NOMS ACB (FONCTION)  
  
-   ACBFUNCN - NOM DE LA FONCTION ACB  
  
-   ACBINT01 - TEST INTEGER TYPE 01  
  
-   ACBLIB - CONTROL BROKER LIBRARY  
  
-   ACBMATH01 - TEST MATH TYPE 01  
  
-   ACBNEWS - ACB NEW STATUS  
  
-   ACBORDER - ACB ORDER NUMBER  
  
-   ACBPRC - ACB ITEM PRICE  
  
-   ACBPROD - ACB PRODUCT ID  
  
-   ACBQTY - ACB ITEM QUANTITY  
  
-   ACBRES - ACB RESULT INDICATOR  
  
-   ACBSTAT - ACB STATUS  
  
-   ACBSTR01 - TEST STRING TYPE 01  
  
-   ACBTEST - ACB TEST SCREEN  
  
-   ACBTEST2 - ACB TEST ÉCRAN 2  
  
-   ACBTEST3 - ÉCRAN DE TEST ACB 3  
  
-   B5500900 - CONTROL BROKER SUPPORT MODULE  
  
-   D5500900 - STRUCTURE DE DONNÉES DE SERVICE BROKER DE CONTRÔLE  
  
-   D5500900A - STRUCTURE DE DONNÉES DE SERVICE BROKER DE CONTRÔLE  
  
-   D5500900B - STRUCTURE DE DONNÉES DE PRIX FETCH  
  
-   D5500900C - GET CUSTOMER STATUS DATA STRUCTURE  
  
-   D5500900D - STRUCTURE DE DONNÉES L’ÉTAT CLIENT ENSEMBLE  
  
-   D5500900E - STRUCTURE DE DONNÉES L’ÉTAT COMMANDE MISE À JOUR  
  
-   D5500900F - TEST INTEGER  
  
-   D5500900G - CHAÎNE DE TEST  
  
-   D5500900H - DATE DE TEST  
  
-   D5500900I - TEST CHAR  
  
-   D5500900J - TEST MATH NUMERIC  
  
-   D5500900K - TEST DATE 2  
  
#### <a name="customize-the-jdeinteropini-file"></a>Personnaliser le fichier jdeinterop.ini  
 Les classes de connecteur JD Edwards OneWorld XE dans Connector.jar et Kernel.jar requièrent que vous utilisez le fichier de configuration jdeinterop.ini. Ce fichier est défini par le logiciel JD Edwards OneWorld et utilise sa terminologie. Version de Guide interopérabilité JD Edwards OneWorld peut fournir plus d’informations sur l’objectif et la terminologie de ce fichier. Il existe un exemple de fichier jdeinterop.ini dans *< installation_adaptateur > \config\jde*.  
  
Mettre à jour jdeinterop.ini pour faire correspondre les valeurs de paramètre que vous avez définie dans le **propriétés du Transport** écran. Plusieurs systèmes logiques JD Edwards OneWorld peuvent partager le même fichier jdeinterop.ini si leurs paramètres sont compatibles. En règle générale, si deux systèmes logiques pointent vers deux ordinateurs JD Edwards OneWorld différents, ils ont besoin de deux copies différentes du fichier jdeinterop.ini.  
  
> [!NOTE]
>  La journalisation dans jdeinterop.ini doit être désactivée, et les paramètres pour les différents fichiers journaux peuvent être ignorés sans risque.  
  
 Le tableau suivant détaille les paramètres se trouvant dans le fichier jdeinterop.ini. Les informations sont organisées par section. Par exemple, [JDENET] et les sections sont répertoriées dans l'ordre dans lequel ils apparaissent dans le logiciel JD Edwards OneWorld.  
  
#### <a name="jdeinteropini-file-settings"></a>paramètres du fichier jdeinterop.ini
  
|Section|Paramètre et une Description|  
|-------------|-------------------------------|  
|[JDENET]|**EnterpriseServerTimeout.** Valeur de délai d'expiration d'une demande au serveur d'entreprise, en millisecondes. La taille par défaut est 120 000.<br /><br /> **maxPoolSize.** Taille du pool de connexions de socket JDENET. La taille par défaut est 30.|  
|[SERVER]|**glossaryTextServer.** Serveur d'entreprise et port qui fournissent des informations sur le texte de glossaire. Il s'agit du serveur qui retourne des descriptions textuelles des erreurs. C'est souvent le même hôte et le même port que pour le serveur d'applications JD Edwards OneWorld. Il peut y avoir plusieurs serveurs de glossaire pour différents codages linguistiques pris en charge. Par exemple, JDED:6010 ou actsrv1:6009. Les valeurs doivent correspondre à celles définies dans la définition du système.<br /><br /> **codePage.** Le schéma d’encodage. La valeur par défaut est 1252.<br /><br /> -1252 anglais et Europe occidentale<br /><br /> -Japonais 932<br /><br /> -Chinois traditionnel 950<br /><br /> -936 Chinois simplifié<br /><br /> -949 Coréen|  
|[LOGS]|**log= c:\jas.log.** Emplacement du fichier journal. Vous pouvez ignorer sans risque cette erreur.<br /><br /> **debuglog= c:\jasdebug.log.** Emplacement du fichier journal de débogage. Vous pouvez ignorer sans risque cette erreur.<br /><br /> **Debug.** Détermine si le débogage de JDENET est activé. La valeur par défaut est FALSE.|  
|[DEBUG]|**JobFile= c:\Interop.log.** Emplacement du fichier d'erreur. Vous pouvez ignorer sans risque cette erreur.<br /><br /> **DebugFile= c:\InteropDebug.log.** Emplacement du fichier de débogage. Vous pouvez ignorer sans risque cette erreur.<br /><br /> **log= c:\net.log.** Emplacement du fichier journal. Vous pouvez ignorer sans risque cette erreur.<br /><br /> **debugLevel = 0 - 12.** Niveaux de débogage. Vous pouvez ignorer sans risque cette erreur. Il définit le niveau de suivi fourni par le connecteur COM et le composant Callobject dans le fichier journal spécifié, dans le serveur COM uniquement.<br /><br /> -0 aucun. La journalisation est désactivée et seules les erreurs sont écrites dans le fichier JobFile.<br /><br /> -2 erreurs (messages d’erreur)<br /><br /> -4 erreurs système (messages d’exception)<br /><br /> -Informations d’avertissement 6<br /><br /> -Min 8 Trace (opérations clés. Par exemple, Connexion, Déconnexion, Appels de fonctions commerciales.)<br /><br /> -Les informations de dépannage (aide) 10.<br /><br /> -12 informations de débogage complètes (consigne tout)<br /><br /> -Par défaut, il est inutile d’activer le suivi, mais le suivi est utile lorsque vous déboguez votre code.<br /><br /> -NetTraceLevel = 0. Niveaux de suivi. Vous pouvez ignorer sans risque cette erreur. Définit le niveau de suivi fourni par le composant ThinNet dans le fichier journal spécifié, dans le serveur COM uniquement. Les valeurs impaires sont réservées pour les futurs niveaux à ajouter.<br /><br /> -La liste suivante décrit encore plus les niveaux de débogage :<br /><br /> -0 aucun suivi<br /><br /> -1 fait référence à l’ID de processus d’enregistrement, ID de thread et l’état de socket disponible lorsqu’une nouvelle connexion est ajoutée, et le pool de sockets est recherché.<br /><br /> -2 inclut les informations de niveau de suivi 1 et suit également chaque appel effectuée dans la classe de gestionnaire de connexions.<br /><br /> -3 inclut toutes les informations de trace de niveau 2 et également les appels à getPort() et les appels à getHost().|  
|[INTEROP]|**enterpriseServer.** Cette valeur est le nom du serveur hôte. Assurez-vous que cette valeur est la même valeur que vous entrez dans la **nom d’hôte** champ le **informations d’identification JDE** section **définition de système** dans le  **Propriétés du transport** boîte de dialogue. La valeur par défaut est JDED.<br /><br /> **port.** Cette valeur est le numéro de port utilisé pour échanger des données. Assurez-vous que cette valeur est la même valeur que vous entrez dans la **numéro de Port** champ le JD Edwards **informations d’identification** section dans le **propriétés du Transport, la définition de système**. Par exemple, 6010 ou 6009. Les valeurs doivent correspondre à celles définies **définition système**.<br /><br /> **inactive_timeout**. Valeur de délai d'expiration, en millisecondes, pour une transaction en mode de validation automatique. Si l'utilisateur est inactif pendant cette période (en millisecondes), le serveur d'interopérabilité déconnecte l'utilisateur. Vous pouvez modifier cette valeur pour définir une période plus courte. La valeur par défaut est 1200000.<br /><br /> **manual_timeout.** La valeur de délai d’attente en millisecondes pour une transaction en mode de validation manuelle. La valeur par défaut est 120000.<br /><br /> **Repository.** Pointe vers l'emplacement du répertoire contenant Connector.jar et Kernel.jar. Sous UNIX, il s'agit d'un chemin d'accès complet.|  
|[CORBA]|Vous pouvez ignorer sans risque cette erreur.<br /><br /> **Multithread.** Le paramètre peut être ignoré. Valeur 1 pour la prise en charge multithread de CORBA.<br /><br /> Objects= CORBA::Connector;CORBA::OneWorldVersion<br /><br /> Définit les objets que le serveur CORBA doit créer au démarrage. Remplace également - DIORFILENAME = option de ligne de commande, par exemple : CORBA::Connector=connector.ior.|  
  
## <a name="jd-edwards-enterpriseone"></a>JD Edwards EnterpriseOne  
Cette section comprend des informations essentielles sur l’utilisation de l’adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne avec BizTalk Server.
  
### <a name="execute-a-jd-edwards-enterpriseone-master-business-function"></a>Exécuter une fonction commerciale principale de JD Edwards EnterpriseOne  
 Vous pouvez utiliser l'adaptateur BizTalk pour JD Edwards EnterpriseOne pour appeler une fonction commerciale principale JD Edwards EnterpriseOne, telle que Carnet d'adresses, Bon de commande ou Commande client. Vous pouvez également utiliser l'adaptateur dans le cadre d'un effort d'intégration pour se connecter JD Edwards EnterpriseOne avec BizTalk Server.  
  
##### <a name="access-data-stored-in-jd-edwards-enterpriseone"></a>Accéder aux données stockées dans JD Edwards EnterpriseOne  
 L’adaptateur accepte les messages XML pour permettre aux applications de BizTalk Server de communiquer et d’échanger des transactions JD Edwards EnterpriseOne en utilisant l’une des opérations suivantes :  
  
-   **Adaptateur de transmission**, qui utilise un port d’envoi de sollicitation-réponse statique pour envoyer un message à JD Edwards EnterpriseOne et attend une réponse.    
-   **Adaptateur de réception**, qui utilise un port de réception unidirectionnel statique pour recevoir des messages à partir de JD Edwards EnterpriseOne.  
  
### <a name="interoperability-framework"></a>Structure d’interopérabilité  
 JD Edwards EnterpriseOne permet l'intégration à des systèmes via son infrastructure d'interopérabilité. L’adaptateur utilise l’infrastructure JD Edwards EnterpriseOne et tire parti de l’intégration de différentes méthodes d’accès pour fournir davantage de souplesse et de fonctionnalités.  
  
 L'adaptateur BizTalk pour JD Edwards EnterpriseOne prend en charge les méthodes d'accès à l'intégration suivantes :  
  
-   JD Edwards EnterpriseOne ThinNet API    
-   JD Edwards EnterpriseOne XML    
-   les tables de transactions (tables Z) non modifiées JD Edwards EnterpriseOne transaction.  
  
 L'adaptateur utilise l'API JD Edwards EnterpriseOne ThinNet pour communiquer avec l'application JD Edwards EnterpriseOne. L'API ThinNet permet à l'adaptateur d'appeler une fonction commerciale principale (MBF, Master Business Function) dans une unité de travail (UOW, Unit Of Work) unique. Lorsqu'une fonction MBF échoue, l'ensemble de l'unité de travail échoue. Cela empêche les mises à jour partielles. La validation des données, les règles d'entreprise et les communications vers la base de données sous-jacente sont gérées par l'application JD Edwards EnterpriseOne.  
  
#### <a name="jd-edwards-outbound-processing-framework"></a>Infrastructure de traitement sortant de JD Edwards  
 Dans le processus sortant, l'événement démarre lorsqu'une fonction MBF spécifique est exécutée dans l'environnement JD Edwards EnterpriseOne. La fonction MBF écrit les informations requises pour l'événement dans la table d'interface appropriée, puis notifie la fonction de traitement par lots (BF, Batch Function) du sous-système qu'un événement s'est produit. Ensuite, la fonction BF du sous-système inclut une entrée relative à l'événement dans la file d'attente des données du sous-système.  
  
 Le sous-système sortant récupère l'entrée de la file d'attente des données et recherche dans la table de contrôle d'exportation des données les processus externes à notifier. Le sous-système sortant appelle ensuite l'écouteur de l'adaptateur BizTalk pour JD Edwards EnterpriseOne avec une notification. L'écouteur passe la notification au générateur. Le générateur utilise alors l'API JD Edwards EnterpriseOne ThinNet pour récupérer les informations appropriées dans la table d'interface.  
  
### <a name="set-string-justification-in-jdearglist"></a>Jeu de justification des chaînes dans Jdearglist  
 Pour configurer certains arguments de chaîne comme alignés à droite et gauche d’un remplissage dans le J.D. Fichier de jdearglist.txt Edwards EnterpriseOne, vous devez connaître les fonctions commerciales que vous souhaitez accéder ; plus précisément, vous devez connaître les champs de la fonction d’entreprise que vous souhaitez appeler.  
  
 Vous devez mettre à jour le fichier jdearglist.txt avant de générer les liaisons (schémas) dans l'orchestration. Les instructions de mise à jour le fichier jdearglist.txt décrit dans la section « Gestion des valeurs de chaîne ».  
  
 Si vous recevez un message d’avertissement jdearglist.txt dans le journal, son objectif est de vous informer que le fichier jdearglist.txt est manquant. Toutefois, si vous exécutez la fonction d’entreprise SalesOrder ou PurchaseOrder, vous devez disposer de ce fichier dans votre chemin d’accès ou il ne fonctionne pas.  
  
### <a name="understand-jdeinteropini"></a>Comprendre les jdeinterop.ini  
 Les classes de connecteur JD Edwards EnterpriseOne dans Connector.jar et Kernel.jar requièrent que vous utilisez un fichier de configuration nommé jdeinterop.ini. Ce fichier est défini par le logiciel JD Edwards EnterpriseOne et utilise sa terminologie. Pour plus d’informations sur l’objectif et la terminologie de ce fichier, consultez le Guide de l’interopérabilité JD Edwards. Il existe un exemple de fichier jdeinterop.ini dans : Program Files\Microsoft Microsoft BizTalk Adapters for Enterprise applications\jd Edwards EnterpriseOne(r) \config.  
  
 Il n’est pas recommandé de modifier manuellement ce fichier, car il interagit avec le **propriétés du Transport** boîte de dialogue pour le port d’envoi--par exemple, les champs marqués comme **< configurés par BizTalk\>** .  
  
## <a name="peoplesoft-enterprise"></a>PeopleSoft Enterprise  
Cette section comprend des informations essentielles sur l’utilisation de l’adaptateur Microsoft BizTalk pour PeopleSoft Enterprise avec BizTalk Server.
  
### <a name="receive-handler-peoplesoft-requirements"></a>Configuration requise de PeopleSoft Gestionnaire de réception  
 PeopleSoft Integration Broker doit pouvoir communiquer avec BizTalk Server. Les opérations suivantes peuvent avoir déjà été effectuées dans un environnement PeopleSoft existant, et vous pouvez réutiliser un nœud existant. Dans ce cas, vous n'avez pas besoin de faire autre chose excepté obtenir les spécifications HTTP d'un administrateur système PeopleSoft. Pour plus d’informations, consultez la documentation de PeopleSoft.  

Les étapes suivantes fournissent une vue d’ensemble dans PeopleSoft :  
  
1.  Le message et l’active par le biais du Concepteur d’applications.  
  
2.  Apportez une modification unique au fichier integration.gateway.properties de PeopleSoft.  
  
3.  Créez et configurez la passerelle et les nœuds pour activer HTTP :
  
    -   Le nœud doit utiliser une méthode de déclenchement, par exemple le mécanisme LOCATION_SYNC.   
    -   Le nœud doit utiliser HTTP.    
    -   Le nœud doit pointer vers l'hôte et le port auxquels vous envoyez l'événement.  
  
### <a name="send-handler-peoplesoft-requirements"></a>Configuration requise de PeopleSoft Gestionnaire d’envoi  
 L’adaptateur BizTalk pour PeopleSoft Enterprise se compose d’une interface de composant personnalisée (CI) qui fournit l’accès via une API Java. Un objet de l’élément de configuration personnalisé, **GET_CI_INFO**, est déployé dans le système PeopleSoft à l’aide des outils de PeopleSoft, pour fournir des informations de métadonnées qui sont requis par l’adaptateur BizTalk pour PeopleSoft Enterprise. Pour plus d’informations, reportez-vous à la documentation de PeopleSoft.  
  
 Le téléchargement de l'interface de composant personnalisée n'intervient qu'une fois. Ce fichier, GET_CI_INFO.pc, est fourni avec le produit et doit être installé dans le système PeopleSoft pour que vous puissiez utiliser l'adaptateur pour parcourir les interfaces de composant. Vous devez avoir accès au Concepteur d’applications PeopleSoft ; Toutefois, le Concepteur d’applications ne doivent pas se trouvent à proximité de l’ordinateur BizTalk Server. Le Concepteur d’applications vous permet de télécharger l’élément de configuration personnalisé dans l’ordinateur PeopleSoft que vous recherchez.  
  
 Vous devez avoir accès à l’ordinateur PeopleSoft, car vous devez définir la variable d’environnement CLASSPATH (ou définir les informations dans le **propriétés du Transport** fenêtre) pour pointer vers le fichier PSJOA/psjoa.jar de PeopleSoft.  
  
### <a name="set-environment-variable-and-use-component-interface"></a>Définir la variable d’environnement et utilisez l’interface de composant  
Pour plus d’informations sur PeopleSoft, consultez la documentation de PeopleSoft.  
  
#### <a name="set-classpath-environment-variable"></a>Définir la variable d’environnement ClassPath  

**Mise à jour de JAVA_HOME**    
  
 Définissez la variable JAVA_HOME de façon à pointer vers votre installation JDK, par exemple :  
  
```  
set JAVA_HOME=C:\j2sdk1.4.2_06  
```  
  
 **Mise à jour de CLASSPATH**  
  
Pour utiliser les interfaces de composant (PeopleSoft 8 uniquement) vous devez mettre à jour votre variable CLASSPATH pour inclure l’interface de composant PeopleSoft un fichier jar :
  
1.  Dans **le panneau de configuration**, ouvrez **système**.  
  
2.  Sur le **avancé** onglet, sélectionnez **Variables d’environnement**, puis sélectionnez **CLASSPATH**.  
  
3.  Ajoutez le chemin d’accès. Par exemple, entrez :  
  
    ```  
    <PeopleSoft_Home>\web\PSJOA\psjoa.jar  
    ```  
  
 L'adaptateur BizTalk pour PeopleSoft Enterprise requiert le fichier psjoa.jar. Cette condition est satisfaite lorsque vous créez un port d'envoi. Pour plus d'informations, consultez la section relative à la « Définition de propriétés de transport dans le système PeopleSoft » dans la documentation de l'adaptateur.  
  
> [!NOTE]
>  Vous ne devez avoir qu'un seul de ces répertoires dans votre chemin d'accès (PATH) pour garantir que l'adaptateur BizTalk pour PeopleSoft Enterprise récupère les DLL appropriées. Si votre environnement n'est pas correctement configuré pour la version souhaitée de PeopleSoft, des erreurs difficiles à repérer peuvent être générées.  
  
#### <a name="use-component-interfaces"></a>Utilisez les interfaces de composant  
  
<a name="BKMK_CustomCI"></a>   
##### <a name="upload-a-custom-ci-into-peoplesoft"></a>Télécharger un élément de configuration personnalisée dans PeopleSoft  
 L'adaptateur BizTalk pour PeopleSoft Enterprise requiert une modification de l'application PeopleSoft. Pour utiliser les interfaces de composant, vous devez charger une interface de composant personnalisée, GET_CI_INFO, dans PeopleSoft. Pour utiliser l'adaptateur, vous devez uniquement importer GET_CI_INFO pendant la configuration initiale. L'adaptateur utilise GET_CI_INFO pour obtenir des informations sur les autres interfaces de composant existantes dans PeopleSoft.  
  
 Cette section explique comment importer manuellement une interface de composant personnalisée qui vous permettre de parcourir les interfaces de composant dans PeopleSoft. Notez que les méthodes personnalisées n'utilisent ou ne modifient aucune propriété de l'interface de composant installée. Pour importer l'interface de composant personnalisée, vous pouvez utiliser une des méthodes suivantes :  
  
-   Créez un composant pour importer les méthodes personnalisées.  
  
-   Utilisez un composant existant qui ne contient aucune clé ; par exemple, INSTALLATION_RS.  
  
 L'interface de composant simple ne doit contenir aucune clé. Si vous n'êtes pas sûr qu'une interface de composant particulière contient des clés, vous pouvez exécuter cette instruction SQL simple à l'aide de votre outil de requête SQL. Il vous donne la liste de toutes les interfaces de composant dans votre application qui n’ont aucune clé.  
  
```  
select distinct BCNAME  
from PSBCITEM bc1  
where not exists  
(select 1  
from PSBCITEM bc2  
where bc1.BCNAME = bc2.BCNAME  
and bc2.BCTYPE in (1, 2))  
```  
  
 Vous pouvez suivre la documentation de PeopleSoft pour créer un composant simple unique pour le stockage des méthodes personnalisées de l'adaptateur BizTalk de PeopleSoft Enterprise. Vous pouvez également cloner l'une des interfaces de composant préexistantes et l'utiliser pour stocker les méthodes personnalisées.  
  
 Pour vérifier que votre interface GET_CI_INFO ne contient aucune clé, exécutez l'outil de test de l'interface de composant du Concepteur d'applications de PeopleTools.  
  
<a name="BKMK_NewCom"></a>   
##### <a name="create-a-new-component-interface"></a>Créer une nouvelle interface de composant  
 Suivez ces étapes pour créer une nouvelle interface de composant à l’aide du Concepteur d’applications PeopleSoft :
  
1.  Ouvrez le **Concepteur d’applications PeopleSoft**.  
  
2.  Entrez un type de connexion de trois niveaux, puis cliquez sur **OK**. Par exemple, sélectionnez Serveur d'applications dans la liste.  
  
3.  Dans le Concepteur d’applications, sur le **fichier** menu, sélectionnez **nouveau**.  
  
4.  Dans le **nouveau** boîte de dialogue, sélectionnez **Interface de composant**, puis cliquez sur **OK**.  
  
5.  Cliquez sur **Sélectionner**.  
  
6.  Dans la liste de tous les composants, sélectionnez n'importe quel composant simple. Par exemple, sélectionnez INSTALLATION_RS ou un nouveau composant PeopleSoft que vous avez créé.  
  
 Les méthodes personnalisées ne pas utiliser ou modifier des propriétés de l’interface de composant qu’il est installé dans.  
  
 Cette interface de composant simple ne doit pas contenir de clés. Si vous n'êtes pas sûr qu'une interface de composant particulière contient des clés, vous pouvez exécuter cette instruction SQL simple à l'aide de votre outil de requête SQL. Il vous donne la liste de toutes les interfaces de composant dans votre application qui n’ont aucune clé :  
  
```  
select distinct BCNAME from PSBCITEM bc1 where not exists (select 1 from PSBCITEM bc2 where bc1.BCNAME = bc2.BCNAME and bc2.BCTYPE in (1, 2))  
```  
  
> [!NOTE]
>  Vous pouvez également suivre la documentation de PeopleSoft pour créer un composant simple unique pour le stockage des méthodes personnalisées pour l’adaptateur BizTalk pour PeopleSoft Enterprise.  
  
 Pour vérifier que votre interface GET_CI_INFO ne contient aucune clé, exécutez l'outil de test de l'interface de composant du Concepteur d'applications de PeopleTools.  
  
##### <a name="check-component-interface"></a>Vérifiez l’interface de composant  
 Vous avez terminé le chargement de l'interface GET_CI_INFO de l'adaptateur Microsoft BizTalk pour PeopleSoft dans votre système PeopleSoft. GET_CI_INFO est une interface de composant personnalisée définie par l'utilisateur. Il contient des méthodes définies par l’utilisateur. L'interface de composant GET_CI_INFO vous permet de parcourir les interfaces de composant de votre système PeopleSoft à l'aide de l'Assistant Adaptateur Microsoft. Vous pouvez localiser et développez GET_CI_INFO pour afficher ses méthodes définies par l'utilisateur.  
  
> [!NOTE]
>  Pour plus d’informations sur les méthodes définies par l’utilisateur, consultez « PeopleSoft : composant Interface méthodes définies par l’utilisateur » dans la documentation de l’adaptateur.  
  
##### <a name="set-the-component-interface-security"></a>Définir la sécurité d’interface de composant  
 Après avoir installé l’interface de composant personnalisée GET_CI_INFO PeopleSoft sur PeopleSoft, définissez les paramètres de sécurité pour **GetCINamespace**, **GetDetails**, et **GetCollections**méthodes pour l’adaptateur BizTalk pour PeopleSoft Enterprise. Cette pratique est courante lorsque vous créez des composants personnalisés ou des méthodes définies par l'utilisateur.  
  
> [!NOTE]
>  La procédure suivante décrit la configuration de la sécurité pour toutes les versions prises en charge de PeopleSoft dans tous les modes pris en charge.  
>   
>  Pour configurer la sécurité pour l'interface de composant  
  
1.  Pointez sur **PeopleTools**, pointez sur **sécurité**, pointez sur **autorisations et rôles**, puis sélectionnez **listes des autorisations**.  
  
2.  Dans le **mettre à jour de sécurité** fenêtre, cliquez sur **recherche**, sélectionnez la **liste des autorisations**, puis cliquez sur le lien hypertexte approprié dans la liste.  
  
3.  Dans le **liste des autorisations** volet de droite, cliquez sur la flèche droite à côté du **heures de connexion** onglet à afficher le **Interfaces de composant** onglet.  
  
4.  Cliquez sur le **Interfaces de composant** onglet.  
  
5.  Cliquez sur le signe plus (+) pour ajouter une nouvelle ligne à la **Interfaces de composant** liste.  
  
6.  Sélectionnez le **GET_CI_INFO** interface de composant, puis cliquez sur **modifier**.  
  
7.  Pour définir les méthodes à **un accès complet**, cliquez sur **un accès complet (tous)**, puis cliquez sur **OK**.  
  
8.  Faites défiler vers le bas de la **Interfaces de composant** fenêtre, puis cliquez sur **enregistrer**.  
  
##### <a name="test-the-component-interface"></a>Tester l’interface de composant  
 Vous avez terminé la configuration de la sécurité pour l'interface de composant GET_CI_INFO fournie avec l'adaptateur BizTalk pour PeopleSoft Enterprise. Votre interface de composant PeopleSoft est prête, et vous pouvez parcourir les interfaces de composant PeopleSoft.  
  
 Pour tester l'interface de composant dans le Concepteur d'applications, procédez comme suit :  
  
 Pour tester l’interface de composant  
  
1.  Démarrer le **Concepteur d’applications PeopleSoft**.  
  
2.  Sur le **fichier** menu, pointez sur **ouvrir**, puis sélectionnez **définition = Interface de composant**.  
  
3.  Dans la liste des interfaces de composant, sélectionnez **CI GET_CI_INFO**.  
  
4.  Après avoir ouvert GET_CI_INFO, avec le bouton droit n’importe où dans le volet droit de votre définition d’interface de composant, puis sélectionnez **tester une Interface de composant**.  
  
Le **testeur d’Interface de composant** fenêtre s’ouvre. Aucune clé ne doit être répertoriée. Si votre interface GET_CI_INFO contient les clés, ou s’il existe une autre option pour la sélection, revenez dans le Concepteur d’Application et supprimez toutes les clés de GET_CI_INFO.  
  
## <a name="install-steps"></a>Étapes d’installation
 Avant d’installer, être sûr de BizTalk Server et tous les logiciels requis pour les adaptateurs sont installés. Il est recommandé de fermer toutes les applications avant d'exécuter le programme d'installation.  
  
1.  Exécuter le serveur BizTalk **Setup.exe**, sélectionnez **installer des adaptateurs Microsoft BizTalk**, puis sélectionnez **installer Microsoft BizTalk Adapters for Enterprise Applications**.  
  
    > [!NOTE]
    >  - Vous pouvez également exécuter une installation sans assistance à l’aide de la commande suivante : msiexec /i < msi\> /qn/l * < fichier journal\> --où < fichier journal\> est facultative, mais est utile en cas d’échec de l’installation.  
    >  - L'installation met à jour la variable d'environnement PATH. Pour vous assurer que vous utilisez les variables appropriées, fermez la fenêtre de commande d'installation pour mettre à jour vos variables.  
  
2.  Accepter la **contrat de licence**, puis sélectionnez **suivant**.
  
3.  Entrez votre **informations client**, puis sélectionnez **suivant**.  
  
4.  Sélectionnez un **Complete** ou **personnalisé** installation : 
  
    -   **Complète**: installe tous les adaptateurs Microsoft BizTalk pour les Applications d’entreprise, tous les composants du programme et est utilisée pour le développement et l’exécution.  
  
    -   **Personnalisé**: vous choisissez les cartes et les fonctionnalités que vous souhaitez installer, et où ils sont installés.  
  
    Pour définir la destination, sélectionnez **Parcourir**et définissez le chemin d’installation.  
  
    Sélectionnez **suivant** pour continuer.  
  
5. **Installer**, puis sélectionnez **Terminer** lorsque vous avez terminé.  
  
> [!IMPORTANT]
>  Vous pouvez rencontrer l’erreur suivante lors de l’installation :  
>   
>  `Error 1609. An error occurred while applying security settings. CREATOR OWNER is not a valid user or group`  
>   
>  Pour contourner cette erreur, procédez comme suit, puis réexécutez l’installation :  
>   
>  1. Ouvrez une invite de commandes
>  2. Type : `net user "CREATOR OWNER" /add`. Cela crée un utilisateur appelé CREATOR OWNER.
>  3. Type : `net localgroup Users /add`. Cette opération crée un nouveau groupe appelé utilisateurs.
  
Pour ajouter les adaptateurs dans BizTalk Server, consultez « Ajouter des adaptateurs à l’administrateur de BizTalk » dans cette rubrique.

## <a name="add-adapters-to-biztalk-admin"></a>Ajouter des cartes à l’administrateur de BizTalk
  
> [!NOTE]
>  Si vous installez BizTalk dans un environnement multiserveur (installation du runtime uniquement sur un seul ordinateur et une installation uniquement des outils d’administration sur un autre ordinateur), vous devez installer les adaptateurs BizTalk pour les Applications d’entreprise sur les ordinateurs.  
  
1.  Ouvrez la Console Administration de BizTalk Server, développez **Microsoft BizTalk Server**, puis développez **paramètres de plateforme**.  
  
2.  Avec le bouton droit **cartes**, sélectionnez **nouveau**, puis sélectionnez **carte**.  
  
3.  Entrez un nom, tel que **PeopleSoft**.  
  
4.  Sélectionnez le nom que vous avez entré à partir de la **carte** liste, puis sélectionnez **OK**.  
   
## <a name="post-install---jd-edwards-oneworld"></a>Après l’installation-JD Edwards OneWorld  
 L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld se compose d'un adaptateur de transmission qui crée une interface avec les bases de données et les systèmes serveur pris en charge pour Microsoft BizTalk Server. L’adaptateur de transmission vous permet d’appeler l’appel d’un système serveur à partir de BizTalk Server. La configuration de l'adaptateur de transmission (le Gestionnaire d'envoi d'Administration de BizTalk Server) spécifie l'emplacement de la base de données SQL.  
  
 Consultez la documentation de l'adaptateur pour obtenir des informations sur l'utilisation de l'adaptateur BizTalk pour JD Edwards OneWorld et sur le mappage entre son modèle et le modèle BizTalk Server.  
  
### <a name="single-sign-on"></a>authentification unique (SSO, Single Sign-On)  
 L’adaptateur BizTalk pour JD Edwards OneWorld fournit la prise en charge pour Enterprise Single Sign-On (SSO). Si vous sélectionnez cette option pour utiliser l’authentification unique dans le **propriétés du Transport** page, les informations d’identification pour l’application associée dans la base de données des informations d’identification SSO sont utilisées. Une application associée représente une application/un système principal qui requiert des informations d'identification.  
  
### <a name="installed-components"></a>Composants installés  

* Installation de l’adaptateur installe et inscrit les composants suivants dans le global assembly cache (GAC). Vous pouvez vérifier l’inscription en ouvrant le dossier de l’assembly dans votre Explorateur (< %windir% > \assembly), ou utilisez le `gacutil /l` à partir de l’invite de commandes Visual Studio :

    -   Microsoft.BizTalk.Adapters.BizUtil.dll    
    -   Microsoft.BizTalk.Adapters.JDEProperties.dll    
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll  

  
* btsTask.exe installe et déploie le `Microsoft.BizTalk.Adapters.JDEProperties.dll` fichier dans le GAC. Les résultats de journal de déploiement BizTalk Server se trouvent dans *\Program Files\Microsoft BizTalk Adapters for Enterprise applications\jdedeploy.HTML* et **jdeDeploy.xml**.
  
* Les fichiers spécifiques à l’adaptateur sont installés dans *Program Files* et *Program Files\Common Files*.  
  
* Le `sdk\` est installé dans *Program Files\Microsoft BizTalk Adapters for Enterprise applications\jd Edwards OneWorld*.
  
* * Programme Files\Microsoft BizTalk Adapters pour Enterprise Applications\JD Edwards OneWorld\* contient les fichiers suivants :  
  
    -   classes\JDEJAccess.jar    
    -   Config\JD Edwards OneWorld(r)\BTSREL.exe    
    -   Config\JD Edwards OneWorld(r) \jdearglist.txt    
    -   Config\JD Edwards OneWorld(r) \jdeinterop.ini  
  
* * Programme Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\Bin\* contient les fichiers suivants :  
  
    -   Microsoft.BizTalk.Adapters.JDEProperties.dll    
    -   jdecba.dll  
  
## <a name="post-install---jd-edwards-enterpriseone"></a>Après l’installation-JD Edwards EnterpriseOne  
 L’adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne contient un adaptateur de transmission qui sert d’interface avec les systèmes de serveur à BizTalk Server et les bases de données pris en charge. L'adaptateur de transmission vous permet d'appeler un appel du système serveur à partir de BizTalk Server.  
  
 L’adaptateur BizTalk pour JD Edwards EnterpriseOne fournit la prise en charge pour Enterprise Single Sign-On (SSO). Si vous sélectionnez cette option pour utiliser l’authentification unique dans le **propriétés du Transport** page, les informations d’identification pour l’application associée dans la base de données des informations d’identification SSO sont utilisées. Une application associée représente une application/un système principal qui requiert des informations d'identification.  
  
### <a name="installed-components"></a>Composants installés  
* Installation de l’adaptateur installe et inscrit les composants suivants dans le global assembly cache (GAC). Vous pouvez vérifier l’inscription en ouvrant le dossier de l’assembly dans votre Explorateur (< %windir% > \assembly), ou utilisez le `gacutil /l` à partir de l’invite de commandes Visual Studio :
  
    -   Microsoft.BizTalk.Adapters.BizUtil.dll    
    -   Microsoft.BizTalk.Adapters.JDEProperties.dll    
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll    

* Les fichiers spécifiques à l’adaptateur sont installés dans le *Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\Bin* dossier. Ce dossier contient les fichiers suivants :  
  
    -   Jdecba.dll    
    -   Microsoft.BizTalk.Adapters.JDEProperties.dll  
  
* Les fichiers suivants sont installés dans *Program Files\Microsoft BizTalk Adapters pour applications\j.d d’entreprise. Edwards EnterpriseOne(r)*:  
  
    -   Bin\BTAJDEEnterpriseOneTrace.cmd    
    -   Classes\JDEDynAccess.jar    
    -   Config\btaJDEEnterpriseOneTrace.mof    
    -   Config\jdearglist.txt    
    -   Config\jdeinterop.ini    
    -   Config\jdelog.properties    
    -   Sdk  
  
 
## <a name="post-install---peoplesoft-enterprise"></a>Après l’installation-PeopleSoft Enterprise  
 L’adaptateur Microsoft BizTalk pour PeopleSoft Enterprise contient un adaptateur de transmission qui sert d’interface pris en charge des bases de données et les systèmes de serveur à BizTalk Server. L'adaptateur de transmission vous permet d'appeler un appel du système serveur à partir de BizTalk Server. La configuration de l'adaptateur de transmission (le Gestionnaire d'envoi d'Administration de BizTalk Server) spécifie l'emplacement de la base de données SQL.  
  
 L’adaptateur BizTalk pour PeopleSoft Enterprise fournit la prise en charge pour Enterprise Single Sign-On (SSO). Si vous sélectionnez cette option pour utiliser l’authentification unique dans le **propriétés du Transport** page, les informations d’identification pour l’application associée dans la base de données des informations d’identification SSO sont utilisées. Une application associée représente une application/un système principal qui requiert des informations d'identification.  
  
 Installation de l’adaptateur inclut les exemples dans le répertoire \sdk.  
  
### <a name="installed-components"></a>Composants installés  
* Installation de l’adaptateur installe et inscrit les composants suivants dans le global assembly cache (GAC). Vous pouvez vérifier l’inscription en ouvrant le dossier de l’assembly dans votre Explorateur (< %windir% > \assembly), ou utilisez le `gacutil /l` à partir de l’invite de commandes Visual Studio :
  
    -   Microsoft.BizTalk.Adapters.BizUtil.dll    
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll    

* Les fichiers spécifiques à l’adaptateur sont installés dans *Program Files* et *Program Files\Common Files*. Les fichiers suivants sont installés dans *Program Files\Microsoft BizTalk Adapters pour Enterprise Applications\PeopleSoft Enterprise (r)*:
  
    -   bin\BTAPeopleSoftTrace.cmd    
    -   config\btaPeopleSoftTrace.mof    
    -   config\GET_CI_INFO.pc    
    -   config\GET_CI_INFO.pc    
    -   sdk\  
  
* *Programme Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications* contient les fichiers suivants :  
  
    -   bin\psosa.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreTransmitter.dll  
  
## <a name="post-install-overview---tibco-rendezvous"></a>Vue d’ensemble de post-installation - TIBCO Rendezvous  
 L’adaptateur Microsoft BizTalk pour TIBCO Rendezvous contient recevoir et transmettre des fonctionnalités de l’interface avec les systèmes de serveur à BizTalk Server et les bases de données pris en charge.  
  
-   Le côté réception écoute les appels sortants du système serveur.  
  
-   Le côté transmission vous permet d'appeler un appel du système serveur à partir de BizTalk Server.  
  
 Consultez la documentation de l’adaptateur pour plus d’informations sur l’utilisation de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous et sur le mappage entre son modèle et le modèle de BizTalk Server.  
  
### <a name="installed-components"></a>Composants installés  
* Installation de l’adaptateur installe et inscrit les composants suivants dans le global assembly cache (GAC). Vous pouvez vérifier l’inscription en ouvrant le dossier de l’assembly dans votre Explorateur (< %windir% > \assembly), ou utilisez le `gacutil /l` à partir de l’invite de commandes Visual Studio : 
  
    -   Microsoft.BizTalk.Adapters.TibcoRV    
    -   Microsoft.BizTalk.Adapters.TibcoRV.Common    
    -   Microsoft.BizTalk.Adapters.TibcoRV.Service    
    -   Microsoft.BizTalk.Adapters.TibRV.Properties    
    -   Microsoft.BizTalk.Adapters.TibcoEMS    
    -   Microsoft.BizTalk.Adapters.TibcoEMS.Properties    
    -   Microsoft.BizTalk.Adapters.TibcoRVManagement    
    -   Microsoft.BizTalk.Adapters.TibcoRVReceiver  
    -   Microsoft.BizTalk.Adapters.TibcoRVTransmitter  
  
* Les fichiers spécifiques à l’adaptateur sont installés dans *Program Files et Program Files\Common Files*. Les fichiers suivants sont installés dans *programme Files\Microsoft BizTalk Adapters for Enterprise Applications\ TIBCO Rendezvous(r)*:  
  
    -   bin\BTATibcoRVTrace.cmd    
    -   bin\mbaRV.exe    
    -   bin\Microsoft.BizTalk.Adapters.TibcoRV.Common.dll    
    -   bin\Microsoft.BizTalk.Adapters.TibcoRV.dll    
    -   bin\Microsoft.BizTalk.Adapters.TibcoRV.Service.dll    
    -   bin\Microsoft.BizTalk.Adapters.BizUtil.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   bin\Microsoft.BizTalk.Adapters.CoreTransmitter.dll    
    -   bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll    
    -   Config\btaTibcoRVTrace.mof    
    -   sdk\  
  
* *Programme Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications* contient les fichiers suivants :  
  
    -   bin\tibcorvcba.dll    
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll  
  
### <a name="add-tibcorendezvousdll-to-the-gac"></a>Ajoutez TIBCO. Rendezvous.dll dans le GAC  
 L’adaptateur BizTalk pour TIBCO Rendezvous requiert la **TIBCO. Rendezvous.dll** fichier. La version minimale requise est 1.0.3036.23330 FileVersion, qui est fournie avec la version 8.1. Si cet assembly n'est pas installé, l'adaptateur déclenche une exception et consigne un message approprié.  
  
 Vous devez utiliser la liaison tardive pour charger les assemblys afin que les assemblys TIBCO Rendezvous n’échouent pas lorsqu’une version particulière de la TIBCO. Rendezvous.dll et TIBCO. Module de rendezvous.NET ne sont pas sur l’ordinateur cible.
  
 **Composant d’exécution**  
  
 Vérifiez que le composant d'exécution TIBCO Rendezvous est installé sur votre ordinateur. Le composant d'exécution est le seul composant que vous devez installer lorsque vous installez TIBCO Rendezvous.  

1. Dans une invite de commandes Visual Studio, accédez à l’emplacement de la TIBCO. Fichier de rendezvous.dll. Le chemin d’accès de cette DLL dans l’installation par défaut de TIBCO Rendezvous est **C:\TIBCO\TIBRV\BIN\TIBCO. Rendezvous.dll**.  
  
2. À l'invite de commandes, tapez :  
  
```
C:\TIBCO\TIBRV\BIN > gacutil /i TIBCO.Rendezvous.dll
```
  
 Le fichier TIBCO.Rendezvous.dll figure maintenant dans la liste du GAC. Pour afficher la liste, dans le panneau de configuration, ouvrez **outils d’administration**, ouvrez **Microsoft .NET Framework Configuration**, puis ouvrez **Assembly Cache**.  
  
## <a name="post-install---tibco-enterprise-message-service"></a>Après l’installation-TIBCO Enterprise Message Service  
 L’adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service (EMS) contient recevoir et transmettre des fonctionnalités de l’interface avec les systèmes de serveur à BizTalk Server et les bases de données pris en charge.  
  
-   Le côté réception écoute les appels sortants du système serveur.  

-   Le côté transmission vous permet d'appeler un appel du système serveur à partir de BizTalk Server.  
  
 Consultez la documentation de l’adaptateur pour plus d’informations sur l’utilisation de l’adaptateur BizTalk pour TIBCO EMS et sur le mappage entre son modèle et le modèle de BizTalk Server.  
  
### <a name="installed-components"></a>Composants installés  
* Installation de l’adaptateur installe et enregistre le `Microsoft.BizTalk.Adapters.TibcoEMS.dll` fichier dans le global assembly cache (GAC). Vous pouvez vérifier l’inscription en ouvrant le dossier de l’assembly dans votre Explorateur (< %windir% > \assembly), ou utilisez le `gacutil /l` à partir de l’invite de commandes Visual Studio.
  
* Les fichiers spécifiques à l’adaptateur sont installés dans *Program Files* et *Program Files\Common Files*. Les fichiers suivants sont installés sous *programme Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)*:  
  
    -   bin\BTATibcoEMSTrace.cmd    
    -   Microsoft.BizTalk.Adapters.TibcoEMS.dll    
    -   Config\btaTibcoEMSTrace.mof    
    -   sdk\  
  
* *Programme Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin* dossier contient les fichiers suivants :  
  
    -   Microsoft.BizTalk.Adapters.CoreManagement.dll    
    -   Microsoft.BizTalk.Adapters.CoreReceiver.dll    
    -   Microsoft.BizTalk.Adapters.CoreTransmitter.dll  
  
    > [!NOTE]
    >  Vous devez utiliser une liaison tardive pour charger les assemblys afin que les assemblys TIBCO EMS n'échouent pas lorsqu'une version particulière de la DLL TIBCO.EMS.dll n'est pas présente sur l'ordinateur cible.  
  
### <a name="add-tibcoemsdll-api-to-the-gac"></a>Ajoutez TIBCO. EMS.dll API au GAC  
 L'adaptateur BizTalk pour TIBCO EMS requiert l'ajout de la DLL TIBCO.EMS.dll au GAC. L’adaptateur BizTalk pour TIBCO EMS déclenche une exception et consigne un message approprié si cet assembly n’est pas installé.  
  
1.  Copiez le TIBCO EMS C #API sur votre ordinateur BizTalk.  
  
2.  Dans une invite de commandes Visual Studio, accédez à l’emplacement du fichier de l’API c#.  
  
3.  Dans une invite de commandes Visual Studio, tapez le texte suivant :  
  
    ```
    C:\\<TIBCO EMS Folder\>bin> gacutil /i TIBCO.EMS.dll
    ```
  
 Le fichier TIBCO. EMS.dll figure maintenant dans la liste C:\Windows\assembly. Ou, dans le panneau de configuration, ouvrez **outils d’administration**, ouvrez **Microsoft .NET Framework**, puis ouvrez **Assembly Cache** pour afficher la liste GAC.  
  
 **Limitations**  
  
 L’adaptateur BizTalk pour TIBCO EMS utilise TIBCO. EMS.dll pour communiquer avec le serveur. Voici les limitations lorsque vous utilisez le TIBCO. EMS.dll :  
  
1.  Compression des messages, qui permet au client de TIBCO EMS envoyer des messages à EMS sous une forme compressée, n’est pas disponible.  
  
2.  Le chiffrement des messages entre l’adaptateur et le serveur n’est pas disponible. L'API TIBCO. EMS.dll n'autorise pas le chiffrement SSL à l'aide de la bibliothèque OpenSSL, mais les adaptateurs prennent en charge le protocole SSL avec TIBCO.EMS.dll la version de produit (ProductVersion) 5.0 et les versions ultérieures.  
  
3.  L'API d'administration pour EMS n'est pas prise en charge.  
  
## <a name="adapter-tracing"></a>Suivi des adaptateurs

### <a name="enable-tracing"></a>Activer le suivi
 Il incombe à l'administrateur de choisir le nom de fichier utilisé avec le suivi Windows. L'application écrit dans le système d'exploitation, qui ignore tous les journaux jusqu'à ce que vous souhaitiez les journaux d'un système principal particulier. Pour ce faire, exécutez un fichier de commandes des adaptateurs Microsoft BizTalk pour les applications d'entreprise distinct. L’un des arguments de cette commande est le nom du fichier qui est utilisé pour capturer les informations de trace. Pour plus d’informations, consultez « Événements de trace utiliser Windows » (dans cette rubrique).
  
 Installent des fichiers de trace à * \Program Files\Microsoft BizTalk Adapters for Enterprise Applications\*.  
  
-   bin\BTATrace.cmd    
-   config\btaTrace.mof  
  
### <a name="use-windows-trace-event"></a>Utiliser l’événement de trace Windows  
 Les adaptateurs consignent les messages d'erreur, d'avertissement et d'information dans l'Observateur d'événements Windows. Vous pouvez visualiser des messages de suivi supplémentaires à l'aide de l'outil Suivi d'événements pour Windows (ETW). Lorsqu'ETW est activé, l'outil crée un fichier *.etl pour recevoir les messages. Ce fichier au format binaire doit être converti pour être lu. Pour ce faire, vous devez disposer d’une application consommateur capable d’interpréter le \*fichier .etl, par exemple, Windows tracerpt.exe ou tracedmp.exe.  
  
### <a name="etw-components"></a>Composants de l'outil Suivi d'événements pour Windows
  
 Le Suivi d'événements pour Windows comporte trois composants :  
  
* **Application de contrôleur :** active et désactive un fournisseur. Par exemple, tracelog.exe ou logman.exe.  
  
    Définissez la variable d'environnement PATH de sorte qu'elle pointe vers l'emplacement de tracelog.exe. Cela permet de s’assurer que BTA < nom de l’adaptateur\>suivi des appels de localiser tracelog.exe dans le système. Par défaut, BTA < nom de l’adaptateur\>Trace recherche le chemin d’accès actuel.  
  
    > [!NOTE]
    >  TraceLog.exe est disponible à partir du SDK de Microsoft et est compatible avec les commandes fournies par les adaptateurs Microsoft BizTalk pour les Applications d’entreprise. Pour utiliser logman.exe, consultez la documentation de logman.  
  
* **Application consommateur :** lit les événements enregistrés.  
  
    Pour que l'application consommateur puisse lire les événements du fichier .etl, le Suivi d'événements pour Windows doit les vider dans ce fichier. Généralement, cette opération est effectuée lorsque le contrôleur désactive le suivi.  
  
    Pour utiliser l’application consommateur sans désactiver le suivi, le contrôleur doit activer le suivi avec l’option en temps réel, **< en temps réel\> = -rt**.  
  
* **Fournisseur :** permet de fournir l’événement.  
  
    Chaque adaptateur inclut cinq fournisseurs différents. Ceux-ci sont enregistrés dans WMI (Windows Management Instrumentation). Pour accéder aux fournisseurs enregistrés via le chemin d'accès root\WMI\EventTrace, vous pouvez utiliser des outils tels que WMI CIM Studio.  
  
    Les cinq fournisseurs vous permettent de consigner différents types de messages :  
  
        -   **Receiver Logging Provider**: The <Trace element\> switch is - **receiver**.    
        -   **Receiver CastDetails Provider**: The <Trace element\> switch is - **castDetailsReceive**.    
        -   **Transmitter Logging Provider**: The <Trace element\> switch is - **transmitter**.    
        -   **Transmitter CastDetails Provider**: The <Trace element\> switch is - **castDetailsTransmit**.    
        -   **Management Logging Provider**: The <Trace element\> switch is - **management**.  
  
Pour utiliser ETW, exécutez la commande de l’adaptateur spécifique : `BTA<Adapter Name\>Trace.cmd`. Utilisez-la comme suit :  
  
```  
BTA<Adapter Name>Trace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTA<Adapter Name>Trace <Trace element> -stop  
  
```  
  
 Où :  
  
**< Trace element\>**  (obligatoire) est le type de fournisseur. Les options sont :  
  
 **-castDetailsTransmit**  
  
 **-transmitter**  
  
 **-castDetailsReceive**  
  
 **-receiver**  
  
 **-management**  
  
 **-start, - stop :** activer ou désactiver le fournisseur.  
  
 **-cir < Mo\>:** taille et type de fichier. **-cir** est un fichier circulaire. **< Mo\>:** taille en mégaoctets.  
  
 **-seq < Mo\>:** taille et type de fichier. **-seq** est un fichier séquentiel. **< Mo\>:** taille en mégaoctets.  
  
 **-rt :** définir le mode en temps réel sur.  
  
 **Fichier journal :** nom du fichier journal (la valeur par défaut s’agit de c:\rtlog.etl).  
  
 Par exemple :  
  
```  
BTAXXXTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAXXXTrace -transmitter -stop  
  
```  
  
> [!NOTE]
>  La commande tracerpt.exe vous permet de mettre en forme les fichiers .etl.  

## <a name="next-steps"></a>Étapes suivantes
* [Adaptateur JD Edwards EnterpriseOne](../core/jd-edwards-enterpriseone-adapter.md)
* [Adaptateur JD Edwards OneWorld](../core/jd-edwards-oneworld-adapter.md)
* [Adaptateur PeopleSoft Enterprise](../core/peoplesoft-enterprise-adapter.md)
* [Adaptateur TIBCO Enterprise Message Service](../core/tibco-enterprise-message-service-adapter.md)
* [Adaptateur TIBCO Rendezvous](../core/tibco-rendezvous-adapter.md)
