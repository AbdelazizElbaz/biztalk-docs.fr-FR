---
title: "Étape 1 : Publier les opérations de composant d’entreprise Siebel comme Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acfa0c36-50f1-45c1-9fc2-e5e5cedaa6a0
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe869b76a155acb326420c3d5c29850548d8b7ff
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-publish-the-siebel-business-component-operations-as-a-wcf-service"></a>Étape 1 : Publier les opérations de composant d’entreprise Siebel comme Service WCF
![Étape 1 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** vous pouvez utiliser l’Assistant de développement de services de l’adaptateur WCF pour générer un service WCF qui peut être hébergé dans un environnement d’hébergement telles que Internet Information Services (IIS) ou le Service d’Activation des processus Windows (WAS). Cette rubrique montre comment utiliser l’Assistant pour générer un fichier de service WCF.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’exécuter l’Assistant, vous devez installer les éléments suivants :  
  
-   [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]à l’aide la **Complete** option ou **personnalisé** option (et en choisissant **outils** au sein de cette option). Cela installe le modèle Visual Studio pour l’Assistant développement d’adaptateurs WCF.  
  
-   [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]  
  
-   Le client Siebel requis.  
  
 Pour plus d’informations sur ces conditions préalables, consultez le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] guide d’installation. Le guide d’installation est généralement installé sur \<lecteur d’installation\>: \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.  
  
## <a name="publish-the-siebel-business-components-as-a-wcf-service"></a>Publier les composants d’entreprise Siebel sous la forme d’un Service WCF  
  
1.  Démarrer [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], puis créez un projet.  
  
2.  Dans le **nouveau projet** boîte de dialogue, à partir de la **types de projet** volet, sélectionnez **Visual C#**. À partir de la **modèles** volet, sélectionnez **Service d’adaptateur WCF**.  
  
     Également, dans le **types de projet** volet, développez **Visual C#**, puis sélectionnez **Web**. À partir de la **modèles** volet, sélectionnez **Service d’adaptateur WCF**.  
  
    > [!NOTE]
    >  Si vous avez installé Visual Studio avec le composant développement Web, le **Service d’adaptateur WCF** modèle est également disponible à partir de la **nouveau site Web** option.  
  
3.  Spécifiez un nom et l’emplacement de la solution, puis cliquez sur **OK**. L’Assistant développement d’adaptateurs WCF démarre.  
  
4.  Dans la page d’accueil, cliquez sur **suivant**.  
  
5.  Dans la page Choisir les opérations, spécifiez une chaîne de connexion pour se connecter au système Siebel. Pour cela :  
  
    1.  Dans le **sélectionner une liaison** , cliquez sur **siebelBinding**, puis cliquez sur **configurer**.  
  
    2.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **sécurité** onglet.  
  
    3.  Dans le **type d’informations d’identification du Client** liste, sélectionnez **nom d’utilisateur**, puis spécifiez le nom d’utilisateur et un mot de passe pour se connecter au système Siebel.  
  
    4.  Cliquez sur le **propriétés URI** onglet et spécifiez des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], consultez [Creat l’URI de connexion du système Siebel](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
        > [!NOTE]
        >  Si les paramètres de connexion contiennent des caractères réservés (par exemple, les caractères spéciaux XML), vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Toutefois, si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
    5.  Cliquez sur le **propriétés de liaison** onglet et spécifiez des valeurs pour les propriétés de liaison, si les, requis pour les opérations que vous souhaitez cibler.  
  
         Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
    6.  Cliquez sur **OK**, puis cliquez sur **connexion**. Une fois la connexion est établie, l’état de connexion s’affiche en tant que **connecté**.  
  
6.  Dans la page Choisir les opérations, dans le **type de contrat Select** , cliquez sur **Client (Outbound operations)**.  
  
7.  Dans le **sélectionner une catégorie** , développez le Siebel **des objets métier** nœud pour afficher la liste d’objets métier dans le référentiel Siebel. Pour cet exemple, procédez comme suit :  
  
    1.  Développez le **compte** objet métier, puis cliquez sur le **compte** composant d’entreprise.  
  
    2.  Dans le **catégories et opérations disponibles** boîte, sélectionnez le **requête** opération, puis cliquez sur **ajouter**. L’opération sélectionnée est répertoriée dans le **ajouté des catégories et opérations** boîte.  
  
         ![Sélectionnez les opérations de composant d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/media/ed0cb649-dc4d-49ce-9541-c491c9cc9ac9.gif "ed0cb649-dc4d-49ce-9541-c491c9cc9ac9")  
  
8.  Dans la page Choisir les opérations, cliquez sur **suivant**.  
  
9. Dans la page Configurer le Service et les comportements de point de terminaison, spécifier des valeurs pour configurer le comportement de service et de point de terminaison.  
  
    1.  Dans le **Configuration de comportement de Service** , spécifiez des valeurs pour les éléments suivants :  
  
        |Pour la propriété|Spécifiez la valeur|  
        |----------------------|-----------------------|  
        |EnableMetadataExchange|Affectez la valeur **True** pour créer un point de terminaison de métadonnées exchange. En définissant ce paramètre **True**, vous rendre les métadonnées de service disponible à l’aide de protocoles standardisés, tels que les demandes WS-MEX (Metadata Exchange) et HTTP/GET.<br /><br /> Valeur par défaut est **False**.|  
        |IncludeExceptionDetailsinFault|Affectez la valeur **True** pour inclure des informations d’exception gérées dans le détail des erreurs SOAP retournées au client à des fins de débogage. Valeur par défaut est **False**.|  
        |Nom|Nom de la configuration de comportement de service.|  
        |UseServiceCertificate|Spécifie si vous souhaitez utiliser le mode de sécurité de niveau message WCF. Valeur par défaut est **True**.<br /><br /> Pour ce didacticiel, vous affectez la valeur **False**.|  
        |FindValue|Chaîne qui spécifie la valeur à rechercher dans le magasin de certificats X.509.<br /><br /> **Remarque :** spécifier une valeur pour cette propriété uniquement si **UseServiceCertificate** a la valeur **True**.|  
        |StoreLocation|Une valeur qui spécifie l’emplacement du magasin de certificats que le service peut utiliser pour valider le certificat du client.<br /><br /> **Remarque :** spécifier une valeur pour cette propriété uniquement si **UseServiceCertificate** a la valeur **True**.|  
        |StoreName|Nom du magasin de certificats X.509 à ouvrir.<br /><br /> **Remarque :** spécifier une valeur pour cette propriété uniquement si **UseServiceCertificate** a la valeur **True**.|  
        |X509FindType|Le type de recherche X.509 à exécuter.<br /><br /> **Remarque :** spécifier une valeur pour cette propriété uniquement si **UseServiceCertificate** a la valeur **True**.|  
  
        > [!NOTE]
        >  Pour plus d’informations sur les certificats et les propriétés associées, consultez [X509ClientCertificateCredentialsElement propriétés](https://msdn.microsoft.com/library/system.servicemodel.configuration.x509clientcertificatecredentialselement_properties.aspx).
  
    2.  Dans le **Configuration de comportement de point de terminaison** , spécifiez des valeurs pour les éléments suivants :  
  
        |Pour la propriété|Spécifiez la valeur|  
        |----------------------|-----------------------|  
        |Type d’authentification|-Définissez cette propriété sur **ClientCredentialUserNamePassword** pour activer les clients spécifier le nom d’utilisateur et un mot de passe lors de l’utilisation du service WCF.<br /><br /> -Définissez cette propriété sur **HTTPUserNamePassword** les clients à spécifier le nom d’utilisateur et mot de passe dans le cadre de l’en-tête HTTP.<br /><br /> -Définissez cette propriété sur **automatique** d’abord activer les clients à spécifier les informations d’identification via la **ClientCredential** interface. En cas d’échec, les clients peuvent passer des informations d’identification dans le cadre de l’en-tête HTTP.<br /><br /> Valeur par défaut est **automatique**. Pour Microsoft Office SharePoint Server utiliser le service WCF, vous devez définir en tant que **HTTPUserNamePassword**.|  
        |Nom|Spécifiez un nom pour la configuration de comportement de point de terminaison.|  
        |UsernameHeader|Nom de l’en-tête de nom d’utilisateur. Pour cet exemple, spécifiez **MyUserHeader**. Pour plus d’informations sur les en-têtes HTTP, consultez « Prise en charge pour HTTP et SOAP en-têtes personnalisés » à [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692).<br /><br /> **Remarque :** vous devez spécifier une valeur pour cette propriété si le **Type d’authentification** a la valeur **HTTPUserNamePassword**. Si **Type d’authentification** a la valeur **automatique**, cette propriété est facultative.|  
        |PasswordHeader|Nom de l’en-tête de mot de passe. Pour cet exemple, spécifiez **MyPassHeader**. Pour plus d’informations sur les en-têtes HTTP, consultez « Prise en charge pour HTTP et SOAP en-têtes personnalisés » à [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692).<br /><br /> **Remarque :** vous devez spécifier une valeur pour cette propriété si le **Type d’authentification** a la valeur **HTTPUserNamePassword**. Si **Type d’authentification** a la valeur **automatique**, cette propriété est facultative.|  
  
     L’illustration suivante montre la page Configurer le Service et les comportements de point de terminaison avec les valeurs spécifiées.  
  
     ![Configurer la page de Service et comportements de point de terminaison](../../adapters-and-accelerators/adapter-sap/media/0a286b0c-7f0d-46c5-9b56-29bef3a1deea.gif "0a286b0c-7f0d-46c5-9b56-29bef3a1deea")  
  
10. Dans la page Configurer le Service et les comportements de point de terminaison, cliquez sur **suivant**.  
  
11. Dans la page Configurer la liaison de point de terminaison de Service et l’adresse, le **sélectionner un contrat pour configurer** zone répertorie les contrats pour les composants d’entreprise Siebel pour lequel vous avez sélectionné les opérations sur la page Choisir les opérations. Le **opérations sous le contrat sélectionné** affiche les opérations que vous avez sélectionné pour chaque artefact sur la page Choisir les opérations.  
  
12. Dans le **configurer l’adresse et la liaison pour le contrat** , spécifiez des valeurs pour les éléments suivants :  
  
    |Pour la propriété|Spécifiez la valeur|  
    |----------------------|-----------------------|  
    |Configuration de la liaison|L’Assistant prend uniquement en charge la liaison HTTP de base. Par conséquent, le champ de configuration de liaison est automatiquement rempli pour *System.ServiceModel.Configuration.BasicHttpBindingElement*.<br /><br /> Cliquez sur le bouton de sélection **(...)**  pour modifier les propriétés pour la liaison HTTP. Pour utiliser un canal de communication sécurisé, vous devez toujours définir la **Mode** propriété **Transport**. L’Assistant définit la valeur par défaut pour le **Mode** propriété en tant que **Transport**.<br /><br /> Pour plus d’informations sur les autres liaisons exposé, consultez [BasicHttpBindingElement classe](https://msdn.microsoft.com/library/system.servicemodel.configuration.basichttpbindingelement.aspx).|  
    |Nom du point de terminaison|Spécifiez un nom de point de terminaison pour le contrat.|  
  
     Les autres champs de cette page sont remplis automatiquement selon les valeurs spécifiées dans les pages précédentes.  
  
     Cliquez sur **Appliquer**. Effectuer cette étape pour tous les contrats affichés sous la **sélectionner un contrat pour configurer** boîte.  
  
    > [!NOTE]
    >  Si vous ne spécifiez pas de toutes les valeurs de cette page, les valeurs par défaut sont acceptés pour tous les contrats.  
  
     L’illustration suivante montre la page adresse avec les valeurs spécifiées et configurer la liaison de point de terminaison de Service.  
  
     ![Configurer la liaison de point de terminaison de Service et l’adresse](../../adapters-and-accelerators/adapter-siebel/media/467d3e18-027d-4218-9d72-0740c1f559e3.gif "467d3e18-027d-4218-9d72-0740c1f559e3")  
  
13. Dans la page Configurer la liaison de point de terminaison de Service et l’adresse, cliquez sur **suivant**. La page Résumé répertorie une arborescence des contrats pour les composants d’entreprise Siebel sélectionnés et, sous celui-ci, les opérations sélectionnées pour chaque composant d’entreprise.  
  
14. Passez en revue le résumé, puis cliquez sur **Terminer**.  
  
15. L’Assistant crée un service WCF et ajoute les fichiers suivants à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet :  
  
    1.  fichier .svc. Il s’agit du fichier de service WCF. L’Assistant génère un fichier pour chaque contrat.  
  
    2.  Fichier Web.config.  
  
    3.  Code de service (fichier .cs).  
  
16. Publier le service WCF.  
  
    1.  Vérifiez que SSL est activé pour Internet Information Services (IIS). Consultez [comment faire pour configurer SSL](https://docs.microsoft.com/iis/manage/configuring-security/how-to-set-up-ssl-on-iis).
  
    2.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **publier**.  
  
    3.  Dans le **publier le site Web** boîte de dialogue, spécifiez une URL pour le service WCF. Exemple :  
  
        ```  
        https://<computer_name>/Siebel_Account/  
        ```  
  
    4.  À partir de la **copie** , cliquez sur **tous les fichiers projet**.  
  
    5.  Cliquez sur **Publier**.  
  
17. Vérifiez que le service WCF est publié avec succès.  
  
    1.  Démarrez la Console de gestion de Microsoft IIS. Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Internet Information Services**.  
  
    2.  Accédez au nœud sur lequel vous avez publié le service. Pour le **Siebel_Account** de service, accédez à **Internet Information Services** > **\<nom de l’ordinateur\>**   >  **Sites Web** > **Site Web par défaut** > **Siebel_Account**.  
  
    3.  Dans le volet droit, cliquez sur le fichier BusinessObjects_Account_Account_Operation.svc, puis cliquez sur **Parcourir**.  
  
    4.  La page Web s’affiche avec l’URL pour l’extraction du WSDL. Vous pouvez décider de tester la récupération de métadonnées à l’aide de la commande svcutil. Par exemple, la commande pour récupérer les métadonnées pour le service Siebel_Account est la suivante :  
  
        ```  
        svcutil.exe https://localhost/Siebel_Account/BusinessObjects_Account_Account_Operation.svc?wsdl  
        ```  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous disposez maintenant d’un service WCF pour le composant d’entreprise Siebel. Utilisez l’éditeur de définition de catalogue de données métier pour créer un fichier de définition d’application pour les opérations de composant d’entreprise Siebel. Consultez [étape 2 : créer un fichier de définition d’Application pour les opérations de composant d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/step-2-create-an-application-definition-file-for-siebel-business-component.md) pour obtenir des instructions. Le fichier de définition d’application identifie où sont stockées les données LOB et le format dans lequel il est stocké.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Présentation de données provenant d’un système Siebel sur un site SharePoint](../../adapters-and-accelerators/adapter-siebel/tutorial-1-presenting-data-from-a-siebel-system-on-a-sharepoint-site.md)