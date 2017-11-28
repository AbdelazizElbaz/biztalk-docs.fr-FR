---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 0491ac0f26b19a96d11cf633263010026961c58b
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="adding-the-adapter-to-biztalk-server"></a><span data-ttu-id="3275c-101">Ajout de l’adaptateur à BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3275c-101">Adding the Adapter to BizTalk Server</span></span>
<span data-ttu-id="3275c-102">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld contient les dossiers du gestionnaire de réception et du gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="3275c-102">Microsoft BizTalk Adapter for JD Edwards OneWorld contains both the Receive Handler and Send Handler folders.</span></span> <span data-ttu-id="3275c-103">Le dossier du gestionnaire d'envoi contient BizTalkServerApplication.</span><span class="sxs-lookup"><span data-stu-id="3275c-103">The Send Handler folder contains BizTalkServerApplication.</span></span> <span data-ttu-id="3275c-104">L'adaptateur BizTalk pour JD Edwards OneWorld peut être créé. Il est exécuté de façon In-process avec BizTalk Server et n'est pas exécuté dans un processus d'hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="3275c-104">BizTalk Adapter for JD Edwards OneWorld is creatable; it runs in-process with BizTalk Server and does not run in an isolated host process.</span></span>  
  
 <span data-ttu-id="3275c-105">Pour ajouter l'adaptateur à BizTalk Server, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="3275c-105">Use the following procedure to add the adapter to BizTalk Server.</span></span>  
  
### <a name="to-add-biztalk-adapter-for-jd-edwards-oneworld"></a><span data-ttu-id="3275c-106">Pour ajouter l'adaptateur BizTalk pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="3275c-106">To add BizTalk Adapter for JD Edwards OneWorld</span></span>  
  
1.  <span data-ttu-id="3275c-107">Sur le **Démarrer** menu, pointez sur **Program Files**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server** pour démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration.</span><span class="sxs-lookup"><span data-stu-id="3275c-107">On the **Start** menu, point to **Program Files**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration** to start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
2.  <span data-ttu-id="3275c-108">Développez **Administration de BizTalk Server**, développez **groupe BizTalk**, puis développez **paramètres de plateforme**.</span><span class="sxs-lookup"><span data-stu-id="3275c-108">Expand **BizTalk Server Administration**, expand **BizTalk Group**, and then expand **Platform Settings**.</span></span>  
  
3.  <span data-ttu-id="3275c-109">Avec le bouton droit **cartes**, pointez sur **nouveau**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="3275c-109">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
4.  <span data-ttu-id="3275c-110">Dans le **propriétés de l’adaptateur** boîte de dialogue, tapez un nom pour l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3275c-110">In the **Adapter Properties** dialog box, type a name for the adapter.</span></span> <span data-ttu-id="3275c-111">Par exemple, JDEdwards.</span><span class="sxs-lookup"><span data-stu-id="3275c-111">For example, JDEdwards.</span></span>  
  
5.  <span data-ttu-id="3275c-112">Sélectionnez **JDEOneWorld** à partir de la **carte** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3275c-112">Select **JDEOneWorld** from the **Adapter** list, and then click **OK**.</span></span>  
  
## <a name="verifying-the-adapter"></a><span data-ttu-id="3275c-113">Vérification de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="3275c-113">Verifying the Adapter</span></span>  
 <span data-ttu-id="3275c-114">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, vous pouvez vérifier que l’adaptateur fonctionne correctement en examinant le **système logique** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3275c-114">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, you can verify that the adapter is functioning correctly by looking at the **Logical System** window.</span></span> <span data-ttu-id="3275c-115">Lors de l'installation initiale, cette fenêtre est vide car vous n'avez pas encore établi de connexion au système serveur, ni créé de système logique.</span><span class="sxs-lookup"><span data-stu-id="3275c-115">On initial installation, this window is empty because you have not yet established a connection to the server system, nor have you created any logical systems.</span></span>  
  
#### <a name="to-verify-that-the-adapter-is-running-correctly"></a><span data-ttu-id="3275c-116">Pour vérifier le bon fonctionnement de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="3275c-116">To verify that the adapter is running correctly</span></span>  
  
1.  <span data-ttu-id="3275c-117">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, développez **paramètres de plateforme**, développez **cartes**, puis sélectionnez  **JDEOneWorld**.</span><span class="sxs-lookup"><span data-stu-id="3275c-117">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand **Platform Settings**, expand **Adapters**, and then select **JDEOneWorld**.</span></span>  
  
2.  <span data-ttu-id="3275c-118">Dans le volet détails, cliquez sur **BizTalkServerApplication**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3275c-118">In the details pane, right-click **BizTalkServerApplication**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3275c-119">Cliquez sur l’onglet **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="3275c-119">Click the **Properties** tab.</span></span>  
  
4.  <span data-ttu-id="3275c-120">Définissez les paramètres de connexion SQL.</span><span class="sxs-lookup"><span data-stu-id="3275c-120">Set the SQL Connection parameters.</span></span>  
  
    -   <span data-ttu-id="3275c-121">**Définir des paramètres de base de données SQL -** le nom du serveur SQL et la base de données sont ceux que vous définissez lors de l’installation.</span><span class="sxs-lookup"><span data-stu-id="3275c-121">**Define SQL Database Parameters -** The SQL Server Name and Database are those you set at installation.</span></span> <span data-ttu-id="3275c-122">Il s'agit de la zone de texte dans laquelle vous pouvez redéfinir le serveur et la base de données pour cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3275c-122">This is the text area that you can redefine the server and database for this adapter.</span></span>  
  
5.  <span data-ttu-id="3275c-123">Cliquez sur **fermer** pour quitter le **système logique** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3275c-123">Click **Close** to exit the **Logical System** window.</span></span>  
  
     <span data-ttu-id="3275c-124">La prochaine étape consiste à ajouter un système logique à l'aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3275c-124">Your next step is to add a logical system using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3275c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3275c-125">See Also</span></span>  
 <span data-ttu-id="3275c-126">[Planification et Architecture](../core/planning-and-architecture17.md) </span><span class="sxs-lookup"><span data-stu-id="3275c-126">[Planning and Architecture](../core/planning-and-architecture17.md) </span></span>  
 <span data-ttu-id="3275c-127">[Sécurité de l’adaptateur BizTalk pour JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="3275c-127">[Security in BizTalk Adapter for JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="3275c-128">Ajout de l’adaptateur BizTalk pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="3275c-128">Adding BizTalk Adapter for JD Edwards OneWorld</span></span>](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)