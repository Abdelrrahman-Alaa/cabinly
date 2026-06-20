هراجع useUser وUserAvatar ومسار getCurrentUser. الخطأ واضح إنه user طالع null لحظة ما UserAvatar بيحاول يقرأ user.user_metadata.




Ran 4 commands


المشكلة إن useUser بيرجع user = null لو مفيش session، وUserAvatar بيتعرض جوه الـ header قبل ما يمنع الراوت أو بعد logout. هخليه يتعامل مع حالة عدم وجود مستخدم بدل ما يكسر الشجرة.




Edited a file


ده يمنع الكراش. هراجع ProtectedRoute كمان لأن آخر سطر فيه بيرجع children حتى لو المستخدم مش authenticated، وده ممكن يكون سبب ظهور الـ Header قبل التحويل للوجين.




Ran Get-Content -Path src/ui/ProtectedRoute.jsx







في ProtectedRoute فيه bug صغير: بعد ما يقرر إن المستخدم مش authenticated، لسه بيرجع children. هعدله يرجع null أثناء التحويل بدل ما يرندر التطبيق ويخلي UserAvatar يشتغل بلا user.




Edited a file


كده عالجنا السبب المباشر والسبب اللي كان يسمح للمكوّن يظهر بدون session. هراجع التعديلات النهائية بسرعة.