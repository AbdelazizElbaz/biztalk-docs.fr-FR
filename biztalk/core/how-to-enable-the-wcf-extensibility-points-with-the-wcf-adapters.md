---
title: "Activer les Points d’extensibilité WCF avec les adaptateurs WCF | Documents Microsoft"
description: "Installer des assemblys, configurer le fichier machine.config, ajouter l’extension à l’administrateur de BizTalk, créez emplacement de réception pour activer les points d’extensibilité WCF pour les adaptateurs WCF dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c2af105-5272-4a6a-95d2-066312ab788e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2881ddd83ebeb31a9f5ff3da6ed858f158751d64
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters"></a>Procédure d'activation des points d'extensibilité WCF avec les adaptateurs WCF
Activer les trois points d’extensibilité WCF : extension de comportement, extension d’élément de liaison et extension de liaison, avec les adaptateurs WCF-Custom et WCF-CustomIsolated. Pour ce faire, installez tout d'abord les assemblys implémentant les points d'extensibilité WCF dans le Global Assembly Cache (GAC), modifiez le fichier machine.config sur vos ordinateurs, puis configurez l'adaptateur WCF-Custom ou WCF-CustomIsolated à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
Consultez [extension de WCF](https://docs.microsoft.com/dotnet/framework/wcf/extending/extending-wcf) pour plus d’informations sur les points d’extensibilité WCF.
  
 
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs. [Autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md) fournit plus d’informations.  
  
## <a name="install-assemblies-implementing-a-wcf-extensibility-point-in-the-gac"></a>Installer les assemblys implémentant un point d’extensibilité WCF dans le GAC  
  
1.  Copiez les assemblys implémentant le point d'extensibilité WCF dans un dossier sur votre ordinateur local.  
  
2.  Copiez les assemblys utilisés par le point d'extensibilité WCF (le cas échéant) dans un dossier sur votre ordinateur local.  
  
3.  Démarrer le **invite de commandes Visual Studio**.  
  
4.  Tapez la commande suivante :  
  
     **Gacutil.exe /if «\<**  *chemin d’accès du fichier d’assembly .dll*  **\>»**  
  
5.  Cette procédure installe l'assembly dans le GAC, en remplaçant tout autre assembly existant sous le même nom.  
  
6.  À l'invite de commandes [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], répétez les étapes 4 et 5 sur tous les assemblys que vous avez copiés aux étapes 1 et 2 de cette procédure.  
  
7.  Si vous disposez de plusieurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs d’exécution et d’administration, répétez les étapes 1 à 6 de cette procédure sur tous les ordinateurs.  
  
    > [!NOTE]
    >  Pour activer les points d'extensibilité WCF pour les adaptateurs WCF, l'instance de l'hôte BizTalk exécutant l'adaptateur doit être capable de charger, au moment de l'exécution, les assemblys où les points d'extensibilité WCF sont implémentés.  
  
## <a name="configure-the-machineconfig-file-for-a-wcf-binding-extension"></a>Configurer le fichier machine.config pour une extension de liaison WCF  
  
1.  À une invite de commandes, accédez au répertoire % FrameworkDir%\v4. X.XXXXX\CONFIG, puis ouvrez le **machine.config** fichier à l’aide du bloc-notes.  
  
2.  Dans le bloc-notes, si le fichier machine.config n’a pas la  **\<system.serverModel\>\\< extensions\>**  éléments, ajoutez-les dans le  **\<configuration\>**  élément du fichier machine.config de fichier, puis ajoutez le  **\<bindingExtensions\>**  élément pour une extension de liaison WCF à l’intérieur le  **\<system.serverModel\>\\< extensions\>**  éléments. Par exemple, pour activer une extension de liaison personnalisée, netHttpBinding, ajoutez le code suivant à l’intérieur de la  **\<configuration\>**  élément du fichier machine.config :  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <bindingExtensions>  
          <add name="netHttpBinding" type="Microsoft.Samples.Channels.NetHttpBindingCollectionElement, NetHttpBinding, Version=3.0.0.0, Culture=neutral, PublicKeyToken=5b637b51c4aaa2a8" />  
        </bindingExtensions>        
      </extensions>  
    </system.serviceModel>  
    ```  
  
    > [!NOTE]
    >  - Vous pouvez obtenir les informations pour les assemblys à inscrire à l’aide de la commande, **gacutil /lr** *< assembly_name>*.  
    >  - Consultez [bindingExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/bindingextensions) sur cet élément.
  
3.  Dans le Bloc-notes, enregistrez le fichier machine.config.  
  
4.  Si vous avez plusieurs ordinateurs d'exécution et d'administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], répétez les étapes 1 à 3 de cette procédure sur tous les ordinateurs.  
  
    > [!NOTE]
    >  Vous devez répéter ces étapes sur tous les ordinateurs pour l'infrastructure WCF afin de traiter le point d'extensibilité WCF pour l'instance de l'hôte BizTalk et la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
## <a name="configure-a-wcf-binding-extension-by-using-the-biztalk-administration-console"></a>Configurer une extension de liaison WCF à l’aide de la console Administration de BizTalk  
  
1.  Ouvrez **Administration de BizTalk Server.**  
  
    > [!NOTE]
    >  Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration est déjà ouverte, redémarrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Si vous utilisez l'adaptateur WCF-Custom, dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], développez Paramètres de plateforme, puis Instances de l'hôte, puis redémarrez l'instance de l'hôte BizTalk exécutant l'adaptateur.  
  
3.  Si vous utilisez l'adaptateur WCF-CustomIsolated, dans la console de gestion IIS, redémarrez le pool d'applications associé à l'emplacement de réception WCF.  
  
4.  Si vous souhaitez configurer un emplacement de réception pour utiliser un point d’extensibilité WCF, dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, développez  *\<application BizTalk\>* , développez **emplacements de réception**, puis, dans le volet droit, double-cliquez sur  *\<emplacement de réception\>*.  
  
    -   Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Type** la liste déroulante, sélectionnez **WCF-Custom** ou **WCF-CustomIsolated** selon l’adaptateur WCF que vous souhaitez utiliser, puis cliquez sur **configurer**.  
  
5.  Si vous souhaitez configurer un port d’envoi pour utiliser un point d’extensibilité WCF, dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, développez  *\<application BizTalk\>* , développez **Ports d’envoi**, puis, dans le volet droit, double-cliquez sur  *\<port d’envoi\>*.  
  
    -   Dans le **propriétés de Port d’envoi** boîte de dialogue le **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
6.  Dans la boîte de dialogue Propriétés du transport, sur le **liaison** onglet, sélectionnez l’extension de liaison, puis configurez le reste des paramètres pour le transport.  
  
7.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, fermez toutes les boîtes de dialogue ouvertes en cliquant sur le **OK** boutons et assurez-vous qu’aucun messages d’erreur et le journal des événements erroné s’affichent.  
  
## <a name="configure-the-machineconfig-file-for-a-wcf-binding-element-extension"></a>Configurer le fichier machine.config pour une extension d’élément de liaison WCF  
  
1.  À une invite de commandes, accédez au répertoire % FrameworkDir%\v4. X.XXXXX\CONFIG, puis ouvrez le **machine.config** fichier à l’aide du bloc-notes.  
  
2.  Dans le bloc-notes, si le fichier machine.config n’a pas la  **\<system.serverModel\>\\< extensions\>**  éléments, ajoutez-les dans le  **\<configuration\>**  élément du fichier machine.config de fichier, puis ajoutez le  **\<bindingElementExtensions\>**  élément pour un élément de liaison WCF extension à l’intérieur de la  **\<system.serverModel\>\\< extensions\>**  éléments. Par exemple, pour activer une extension d’élément de liaison personnalisée, droppingInterceptor, ajoutez le code suivant à l’intérieur de la  **\<configuration\>**  élément du fichier machine.config :  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <bindingElementExtensions>  
          <add name="droppingInterceptor" type="Microsoft.ServiceModel.Samples.DroppingServerElement, MessageInterceptor, Version=0.0.0.0, Culture=neutral, PublicKeyToken=098514eef14aa34a"/>  
        </bindingElementExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
    > [!NOTE]
    > - Vous pouvez obtenir les informations pour les assemblys à inscrire à l’aide de la commande, **gacutil /lr** *< assembly_name>*.  
    > - Consultez [bindingElementExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/bindingelementextensions) sur cet élément.
  
3.  Dans le Bloc-notes, enregistrez le fichier machine.config.  
  
4.  Si vous avez plusieurs ordinateurs d'exécution et d'administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], répétez les étapes 1 à 3 de cette procédure sur tous les ordinateurs.  
  
    > [!NOTE]
    >  Vous devez répéter ces étapes sur tous les ordinateurs pour l'infrastructure WCF afin de traiter le point d'extensibilité WCF pour l'instance de l'hôte BizTalk et la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
## <a name="configure-a-wcf-binding-element-extension-by-using-the-biztalk-administration-console"></a>Configurer une extension d’élément de liaison WCF à l’aide de la console Administration de BizTalk  
  
1.  Ouvrez **Administration de BizTalk Server.**  
  
    > [!NOTE]
    >  Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration est déjà ouverte, redémarrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Si vous utilisez l'adaptateur WCF-Custom, dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], développez Paramètres de plateforme, puis Instances de l'hôte, puis redémarrez l'instance de l'hôte BizTalk exécutant l'adaptateur.  
  
3.  Si vous utilisez l'adaptateur WCF-CustomIsolated, dans la console de gestion IIS, redémarrez le pool d'applications associé à l'emplacement de réception WCF.  
  
4.  Si vous souhaitez configurer un emplacement de réception pour utiliser un point d’extensibilité WCF, dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, développez  *\<application BizTalk\>* , développez **emplacements de réception**, puis, dans le volet droit, double-cliquez sur  *\<emplacement de réception\>*.  
  
    -   Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Type** la liste déroulante, sélectionnez **WCF-Custom** ou **WCF-CustomIsolated** selon l’adaptateur WCF que vous souhaitez utiliser, puis cliquez sur **configurer**.  
  
5.  Si vous souhaitez configurer un port d’envoi pour utiliser un point d’extensibilité WCF, dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, développez  *\<application BizTalk\>* , développez **Ports d’envoi**, puis, dans le volet droit, double-cliquez sur  *\<port d’envoi\>*.  
  
    -   Dans le **propriétés de Port d’envoi** boîte de dialogue le **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
6.  Dans la boîte de dialogue Propriétés du transport, sur le **liaison** sous l’onglet du **Type de liaison** la liste déroulante, sélectionnez **customBinding**.  
  
7.  Dans la boîte de dialogue Propriétés du transport, sur le **liaison** onglet, avec le bouton droit de la zone cliente de la **liaison** liste, puis cliquez sur **ajouter une extension**.  
  
8.  Dans le **Extension d’élément de liaison sélectionnez** boîte de dialogue, sélectionnez une extension d’élément de liaison, puis cliquez sur **OK**.  
  
9. Dans la boîte de dialogue Propriétés du transport, sur le **liaison** onglet, ajustez l’ordre des éléments de liaison ajouté dans le **liaison** liste selon le type de l’extension d’élément de liaison ajouté à la étape précédente comme suit :  
  
    -   Dans le **liaison** liste, cliquez sur une extension d’élément de liaison, puis cliquez sur **monter l’extension** ou **descendre l’extension**. L’extension d’élément de liaison la plus faible dans le **liaison** liste correspond au composant du bas de la pile de canaux. L’élément de liaison la plus élevée dans la **liaison** liste correspond à un composant en haut de la pile de communication.  
  
        > [!NOTE]
        >  Consultez [des liaisons personnalisées](https://docs.microsoft.com/dotnet/framework/wcf/extending/custom-bindings) pour plus d’informations sur l’ordre spécifique des éléments de liaison pour la liaison personnalisée.
  
10. Dans la boîte de dialogue Propriétés du transport, configurez le reste des paramètres de transport.  
  
11. Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, fermez toutes les boîtes de dialogue ouvertes en cliquant sur le **OK** boutons et assurez-vous qu’aucun messages d’erreur et le journal des événements erroné s’affichent.  
  
## <a name="configure-the-machineconfig-file-for-a-wcf-behavior-extension"></a>Configurer le fichier machine.config pour une extension de comportement WCF  
  
1.  À une invite de commandes, accédez au répertoire % FrameworkDir%\v4. X.XXXXX\CONFIG, puis ouvrez le **machine.config** fichier à l’aide du bloc-notes.  
  
2.  Dans le bloc-notes, si le fichier machine.config n’a pas la  **\<system.serverModel\>\\< extensions\>**  éléments, ajoutez-les dans le  **\<configuration\>**  élément du fichier machine.config de fichier, puis ajoutez le  **\<behaviorExtensions\>**  élément pour une extension de comportement WCF à l’intérieur de la  **\<system.serverModel\>\\< extensions\>**  éléments. Par exemple, pour activer une extension de comportement personnalisée, schemaValidator, ajoutez le code suivant à l’intérieur de la  **\<configuration\>**  élément du fichier machine.config :  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ad307e213604f592"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
    > [!NOTE]
    >  - Vous pouvez obtenir les informations pour les assemblys à inscrire à l’aide de la commande, **gacutil /lr** *< assembly_name>*.  
    >  - Consultez [behaviorExtensions](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/wcf/behaviorextensions) sur cet élément.
  
3.  Dans le Bloc-notes, enregistrez le fichier machine.config.  
  
4.  Si vous avez plusieurs ordinateurs d'exécution et d'administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], répétez les étapes 1 à 3 de cette procédure sur tous les ordinateurs.  
  
    > [!NOTE]
    >  Vous devez répéter ces étapes sur tous les ordinateurs pour l'infrastructure WCF afin de traiter le point d'extensibilité WCF pour l'instance de l'hôte BizTalk et la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
## <a name="configure-a-wcf-behavior-extension-by-using-the-biztalk-administration-console"></a>Configurer une extension de comportement WCF à l’aide de la console Administration de BizTalk  
  
1.  Ouvrez **Administration de BizTalk Server.**  
  
    > [!NOTE]
    >  Si le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration est déjà ouverte, redémarrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Si vous utilisez l'adaptateur WCF-Custom, dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], développez Paramètres de plateforme, puis Instances de l'hôte, puis redémarrez l'instance de l'hôte BizTalk exécutant l'adaptateur.  
  
3.  Si vous utilisez l'adaptateur WCF-CustomIsolated, dans la console de gestion IIS, redémarrez le pool d'applications associé à l'emplacement de réception WCF.  
  
4.  Si vous souhaitez configurer un emplacement de réception à utiliser un point d’extensibilité WCF, dans la console Administration de BizTalk, développez **groupe BizTalk**, développez  *\<application BizTalk\>* , développez **emplacements de réception**, puis, dans le volet droit, double-cliquez sur  *\<emplacement de réception\>*.  
  
    -   Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Type** la liste déroulante, sélectionnez **WCF-Custom** ou **WCF-CustomIsolated** selon l’adaptateur WCF que vous souhaitez utiliser, puis cliquez sur **configurer**.  
  
5.  Si vous souhaitez configurer un port d’envoi à utiliser un point d’extensibilité WCF, dans la console Administration de BizTalk, développez **groupe BizTalk**, développez  *\<application BizTalk\>*, Développez **Ports d’envoi**, puis, dans le volet droit, double-cliquez sur  *\<port d’envoi\>*.  
  
    -   Dans le **propriétés de Port d’envoi** boîte de dialogue le **Type** la liste déroulante, sélectionnez **WCF-Custom**, puis cliquez sur **configurer**.  
  
6.  Dans la boîte de dialogue Propriétés du transport, sur le **comportement** droit **ServiceBehavior** ou **EndpointBehavior** selon le type de l’extension de comportement puis, dans le **sélectionner une Extension de comportement** boîte de dialogue, sélectionnez l’extension de comportement, puis cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue Propriétés du transport, configurez le reste des paramètres de transport.  
  
8.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, fermez toutes les boîtes de dialogue ouvertes en cliquant sur le **OK** boutons et assurez-vous qu’aucun messages d’erreur et le journal des événements erroné s’affichent.  
  
## <a name="configure-a-wcf-custom-receive-location-with-an-ssl-certificate"></a>Configurer un WCF-Custom emplacement de réception avec un certificat SSL  
  
-   Si un emplacement de réception WCF-Custom se produit à utiliser le pilote du noyau HTTP (HTTP.sys) tels que les **httpsTransport** élément de liaison pour les communications Secure Sockets Layer (SSL), l’emplacement de réception doit disposer d’un certificat inscrit pour chaque socket (combinaison adresse IP/port). Utilisez l'outil HttpCfg.exe pour lier un certificat SSL à un port sur l'ordinateur. Pour plus d’informations, consultez [comment faire : configurer un Port avec un certificat SSL](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate).