### <a name="non-pooled-sql-connections-will-leak-memory-if-not-explicitly-disposed"></a><span data-ttu-id="a0e9a-101">SQL-подключения не в составе пула приводят к утечке памяти, если их явно не удалить</span><span class="sxs-lookup"><span data-stu-id="a0e9a-101">Non-pooled SQL connections will leak memory if not explicitly disposed</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a0e9a-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="a0e9a-102">Details</span></span>|<span data-ttu-id="a0e9a-103">В .NET Framework 4.5 SQL-подключения вне пула, которые не предоставляются явно (с помощью Dispose, Close или использования), приводят к утечке памяти</span><span class="sxs-lookup"><span data-stu-id="a0e9a-103">In the .NET Framework 4.5, non-pooled SQL connections which are not explicitly exposed (via Dispose, Close, or using) will leak memory</span></span>|
|<span data-ttu-id="a0e9a-104">Предложение</span><span class="sxs-lookup"><span data-stu-id="a0e9a-104">Suggestion</span></span>|<span data-ttu-id="a0e9a-105">Эта проблема исправлена в сервисном обновлении .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="a0e9a-105">This issue is fixed in a .NET Framework 4.5 servicing update.</span></span> <span data-ttu-id="a0e9a-106">Чтобы устранить эту проблему, обновите .NET Framework 4.5 или выполните обновление до .NET Framework 4.5.1 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="a0e9a-106">Please update the .NET Framework 4.5, or upgrade to .NET Framework 4.5.1 or later, to fix this issue.</span></span> <span data-ttu-id="a0e9a-107">Кроме того, этой проблемы можно избежать с помощью <xref:System.Data.SqlClient.SqlConnection?displayProperty=name> в шаблоне использования (рекомендованный метод) или путем явного вызова Dispose или Close, когда соединение больше не нужно.</span><span class="sxs-lookup"><span data-stu-id="a0e9a-107">Alternatively, this issue may be avoided by using the <xref:System.Data.SqlClient.SqlConnection?displayProperty=name> in a &#39;using&#39; pattern (which is a best practice) or by explicitly calling Dispose or Close when the connection is no longer needed.</span></span>|
|<span data-ttu-id="a0e9a-108">Область</span><span class="sxs-lookup"><span data-stu-id="a0e9a-108">Scope</span></span>|<span data-ttu-id="a0e9a-109">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="a0e9a-109">Edge</span></span>|
|<span data-ttu-id="a0e9a-110">Версия</span><span class="sxs-lookup"><span data-stu-id="a0e9a-110">Version</span></span>|<span data-ttu-id="a0e9a-111">4.5</span><span class="sxs-lookup"><span data-stu-id="a0e9a-111">4.5</span></span>|
|<span data-ttu-id="a0e9a-112">Тип</span><span class="sxs-lookup"><span data-stu-id="a0e9a-112">Type</span></span>|<span data-ttu-id="a0e9a-113">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="a0e9a-113">Runtime</span></span>|
|<span data-ttu-id="a0e9a-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a0e9a-114">Affected APIs</span></span>|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String%2CSystem.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|
