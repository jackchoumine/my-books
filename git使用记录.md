# git 使用记录



## git diff

### 比较两个分支

`git diff branchA branchB`

```bash
λ git diff auth master
diff --git a/src/views/cluster/detail/horizontal/StepOne.vue b/src/views/cluster/detail/horizontal/StepOne.vue
index 05ce64a..ca46f48 100644
--- a/src/views/cluster/detail/horizontal/StepOne.vue
+++ b/src/views/cluster/detail/horizontal/StepOne.vue
@@ -49,6 +49,18 @@ export default {
           key: 'clusterType',
           defaultValue: this.formData.clusterType || '没有容器'
         },
+        {
+          condition: this.formData.clusterType === '容器集群',
+          title: '实例规格',
+          type: 'text',
+          key: 'specification'
+        },
+        {
+          condition: this.formData.clusterType === '容器集群',
+          title: '磁盘容量',
+          type: 'text',
+          key: 'capacity'
+        },
         {
           title: '节点数量',
           type: 'input-number',
@@ -66,18 +78,6 @@ export default {
               else callback()
             }
           }
-        },
-        {
-          condition: this.formData.clusterType === 'CONTAINER',
-          title: '实例规格',
-          type: 'text',
-          key: 'specification'
-        },
-        {
```
`git diff branchA`

```bash
λ git diff auth
```
```bash
λ git diff auth auth
```

`git diff branchB branchA`

```bash
λ git diff master auth
diff --git a/src/views/cluster/detail/horizontal/StepOne.vue b/src/views/cluster/detail/horizontal/StepOne.vue
index ca46f48..05ce64a 100644
--- a/src/views/cluster/detail/horizontal/StepOne.vue
+++ b/src/views/cluster/detail/horizontal/StepOne.vue
@@ -49,18 +49,6 @@ export default {
           key: 'clusterType',
           defaultValue: this.formData.clusterType || '没有容器'
         },
-        {
-          condition: this.formData.clusterType === '容器集群',
-          title: '实例规格',
-          type: 'text',
-          key: 'specification'
-        },
-        {
-          condition: this.formData.clusterType === '容器集群',
-          title: '磁盘容量',
-          type: 'text',
-          key: 'capacity'
-        },
         {
           title: '节点数量',
           type: 'input-number',
@@ -78,6 +66,18 @@ export default {
               else callback()
             }
           }
+        },
+        {
+          condition: this.formData.clusterType === 'CONTAINER',
+          title: '实例规格',
+          type: 'text',
+          key: 'specification'
+        },
+        {
```
`git diff branchB`

```bash
λ git diff master
diff --git a/src/views/cluster/detail/horizontal/StepOne.vue b/src/views/cluster/detail/horizontal/StepOne.vue
index ca46f48..05ce64a 100644
--- a/src/views/cluster/detail/horizontal/StepOne.vue
+++ b/src/views/cluster/detail/horizontal/StepOne.vue
@@ -49,18 +49,6 @@ export default {
           key: 'clusterType',
           defaultValue: this.formData.clusterType || '没有容器'
         },
-        {
-          condition: this.formData.clusterType === '容器集群',
-          title: '实例规格',
-          type: 'text',
-          key: 'specification'
-        },
-        {
-          condition: this.formData.clusterType === '容器集群',
-          title: '磁盘容量',
-          type: 'text',
-          key: 'capacity'
-        },
         {
           title: '节点数量',
           type: 'input-number',
@@ -78,6 +66,18 @@ export default {
               else callback()
             }
           }
+        },
+        {
+          condition: this.formData.clusterType === 'CONTAINER',
+          title: '实例规格',
+          type: 'text',
+          key: 'specification'
+        },
+        {
```

`git diff master..auth`

给 auth 分支的增加文件描述。

```bash
λ git diff master..auth
diff --git a/src/views/cluster/apply/components/ConfigInfo.vue b/src/views/cluster/apply/components/ConfigInfo.vue
index ff6f927..4791bb1 100644
--- a/src/views/cluster/apply/components/ConfigInfo.vue
+++ b/src/views/cluster/apply/components/ConfigInfo.vue
@@ -2,8 +2,8 @@
  * @Description: 销毁申请页面,配置信息
  * @Author: 周其军
  * @Date: 2019年11月11日 15:13:15
- * @LastEditTime:
- * @LastEditors: Please set LastEditors
+ * @LastEditTime: 2019年12月19日 14:32:59
+ * @LastEditors: 周其军
  -->
 <template>
   <div>
diff --git a/src/views/cluster/detail/horizontal/StepOne.vue b/src/views/cluster/detail/horizontal/StepOne.vue
index ca46f48..4e4ea27 100644
--- a/src/views/cluster/detail/horizontal/StepOne.vue
+++ b/src/views/cluster/detail/horizontal/StepOne.vue
@@ -1,3 +1,10 @@
+<!--
+ * @Description: 集群扩容第一步
+ * @Author:
+ * @Date:
+ * @LastEditTime: 2019年12月19日 14:33:53
+ * @LastEditors: 周其军
+ -->
 <template>
   <div>
     <div class="mg-bt-m" style="margin-left: 80px">
@@ -99,8 +106,6 @@ export default {
         message: `提交成功`
       })
     },
```

`git diff auth..master`

```bash
λ git diff auth..master
diff --git a/src/views/cluster/apply/components/ConfigInfo.vue b/src/views/cluster/apply/components/ConfigInfo.vue
index 4791bb1..ff6f927 100644
--- a/src/views/cluster/apply/components/ConfigInfo.vue
+++ b/src/views/cluster/apply/components/ConfigInfo.vue
@@ -2,8 +2,8 @@
  * @Description: 销毁申请页面,配置信息
  * @Author: 周其军
  * @Date: 2019年11月11日 15:13:15
- * @LastEditTime: 2019年12月19日 14:32:59
- * @LastEditors: 周其军
+ * @LastEditTime:
+ * @LastEditors: Please set LastEditors
  -->
 <template>
   <div>
diff --git a/src/views/cluster/detail/horizontal/StepOne.vue b/src/views/cluster/detail/horizontal/StepOne.vue
index 4e4ea27..ca46f48 100644
--- a/src/views/cluster/detail/horizontal/StepOne.vue
+++ b/src/views/cluster/detail/horizontal/StepOne.vue
@@ -1,10 +1,3 @@
-<!--
- * @Description: 集群扩容第一步
- * @Author:
- * @Date:
- * @LastEditTime: 2019年12月19日 14:33:53
- * @LastEditors: 周其军
- -->
 <template>
   <div>
     <div class="mg-bt-m" style="margin-left: 80px">
@@ -106,6 +99,8 @@ export default {
         message: `提交成功`
       })
     },
```

```bash
git diff branchA..branchB
git diff branchA branchB
git diff branchA # 省略后面的分支 就是当前分支
```

比较两个分支文件的差异，可理解为，`branchB 最新版本减去 branchA 最新版本的`。

```bash
git diff # 本地文件和暂存区的比较的 index 
```

```bash
git diff --staged # 最近提交和暂存去比较 index
```



[用 diff 来检查改动]( https://www.git-tower.com/learn/git/ebook/cn/command-line/advanced-topics/diffs )

[git diff　解释]( https://gitguys.com/topics/git-diff-command-explained/ )

[git diff 文件比较]( [https://dzone.com/articles/git-tutorial-%E2%80%93-comparing-files](https://dzone.com/articles/git-tutorial-–-comparing-files) )

```ba
λ git diff --no-index index.js serviceTreeRouter.js
diff --git a/index.js b/serviceTreeRouter.js
index 5910de0..1916236 100644
--- a/index.js
+++ b/serviceTreeRouter.js
@@ -1,345 +1,305 @@
 /*
  * @Description: In User Settings Edit
- * @Author: your name
- * @Date: 2019-10-22 10:29:09
- * @LastEditTime: 2019年12月19日 15:59:52
+ * @Author: huangmei
+ * @Date: 2019-11-27
+ * @LastEditTime: 2019年12月19日 15:58:59
  * @LastEditors: 周其军
  */
-import Vue from 'vue'
-import Router from 'vue-router'
-import { ErrorPage } from '@oppo/cloud-portal-common'
-import serviceTree from './serviceTreeRouter'
-
 const RouterViewHoc = {
   name: 'RouterViewHoc',
   render(h) {
     return h('router-view')
   }
 }
-
-Vue.use(Router)
-
-const router = new Router({
-  mode: 'history',
-  scrollBehavior(to, from, savedPosition) {
-    if (savedPosition) {
-      return savedPosition
-    } else {
-      return { x: 0, y: 0 }
-    }
-  },
-  routes: [
-    {
-      path: '/',
-      redirect: '/kafka-cloud-front/cluster/'
-    },
-    {
-      path: '/kafka-cloud-front/',
-      redirect: '/kafka-cloud-front/cluster/'
+const serviceTreeRouter = [
+  {
+    path: 'serviceTreeCluster',
+    name: 'serviceTreeCluster',
+    meta: {
+      title: '集群管理',
+      menuLinkGroup: true,
```

## git diff

```bash
git diff [filename] # 比较工作区（仓库目录）和暂存区
git diff --cached [filename] # 比较暂存区（索引）和 HEAD(最后一次提交)
git diff --staged [filename] # 同上
git diff HEAD [filename] # 比较 HEAD 和工作区或暂存区，更像前两个的合并功能
git diff master..branchA # 获取在branchA上存在，在master上不存在的内容
git diff commitID1..commitID2 # 比较提交的区别
```

### 比较结果解读

![diff 比较结果解读](https://www.git-tower.com/learn/media/pages/git/ebook/cn/command-line/advanced-topics/diffs/2140873840-1575572522/example-diff.jpg)

#### 比较的文件

为了清楚的显示比较信息，diff 总是把要比较的文件定义成 “a” 和 "b"。

 在大多数情况下 A 和 B 会是项目中的同一个文件，但它们是基于不同的版本。当然 diff 操作也可以比较两个完全没有关联的文件，并显示出它们之间的差别，但是这种操作并不会被经常使用到。 

#### 元数据

`index bbe710..9b62295 100644`，`5910de0..1916236`表示两个文件的HASH ID，表示文件的特定版本。`100644`表示文件类型，100644 普通文件，100755 可执行文件， 120000 仅仅是一符号链接 。

#### 文件标识

 继续向下观察这些输出信息，A 与 B 的真正差别会被显示在这里。为了区分它们，A 和 B 都被赋予了它们特有的符号：对于版本 A，它的符号是一个减号（“-”）；而对于版本 B ，它会使用一个加号（“+”）。 

#### 区块

`@@` 开头到下一个`@@`结束部分叫区块(chunk)，出来表明代码更改的具体行，还提示了更改出的上下文环境，方便快速定位到更改处和改更的含义。

##### 区块头

区块头显示哪些行存在差异。

```bash
@@ -725,3 +725,32 @@ WeakSet 和 Set 的差异：
 4. 没有 `forEach`方法；
 5. 无 `size`属性。

+
+### ES6 Map
+
+Map 是键值对的有序表，键和值可以是任意类型。
```

> 版本a(文件a) 【标记为 - 】，从第 725 行之后的3行代码。
>
> 版本b(文件b)【标记为 +】, 从第725 行之后的 32 行代码。

`@@` 之后表改动上下文环境。

##### 改动内容

改动上下文之后是改的内容，也是使用`-`和`+`表示来是版本a或者b ，通常`-`代表老的内容，`+`表示新的内容。

`git diff A..B`可理解为b版本减去a版本的结果，就容易理解从a到b有哪些变化了。

## git switch 

分支操作可使用该命令进行。

```bash
git switch branchA # 切换到 branchA 会导致本地更改丢失 使用 -f --force --discard-changes 强制切换
git switch -f branchA
# 操作结果
λ git switch -f branchA
Switched to branch 'branchA'

git switch -m branchA # 当前更改合并到切换后的 branchA
# 操作结果类似
λ git switch -m master
Switched to branch 'master'
M       src/main.js

git switch - # 切换到之前的分支并合并更改，在两个分支之间切换时很方便

git switch -c new-branch # 新建分支，会自动检测远程的同名分支，存在从远程分支创建，否则从当前分支创建,本地更改会被带到新分支上
git branch new-branch # 同上
git switch -c new-branch commitId # 从某个提交从新建分支
```
## git checkout
checkout 也能进行分支操作，较新版本的git支持switch，老版本使用 checkout。
```bash
git checkout branchA # 切换分支
git checkout - #切换之前的分支并合并本地更改
git checkout -b new-branch commitId # 从某个提交新建分支 有本地更改未提交，不会成功
git checkout -b new-branch tag # 从tag创建分支
```
