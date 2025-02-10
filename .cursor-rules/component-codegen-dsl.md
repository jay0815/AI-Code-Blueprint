(defparameter *antd-component-codegen*
  '(
    ;; 项目基本信息
    (name "component-codegen-dsl")
    (description "根据设计稿或自然语言需求生成基于 private-component 的 React 业务组件")

    ;; React 业务组件生成提示词
    (react-component-generation
     (demand "[在这里描述设计稿或自然语言需求]"))

    ;; 技术要求
    (technical-requirements
     (stack ("React" "TailwindCSS" "private-component"))
     (typescript t)
     (pure-presentational "组件必须是纯展示组件，所有数据操作通过 props 暴露给外部")
     (state-separation "遵循前后端状态分离原则"))

    ;; 文件结构要求
    (file-structure-requirements
     (component-tsx
      (path "[ComponentName]/[ComponentName].tsx")
      (description "主组件文件：使用函数式组件；从 interface.ts 导入类型定义；实现组件的 UI 和交互逻辑")
      (required t))  ;; 必须生成的文件
     (interface-ts
      (path "[ComponentName]/interface.ts")
      (description "类型定义文件：定义组件的 props 接口；定义组件内部使用的类型")
      (required t))  ;; 必须生成的文件
     (helpers-ts
      (path "[ComponentName]/helpers.ts")
      (description "工具函数文件：抽离可复用的业务逻辑；纯函数实现，不包含副作用")
      (required t))  ;; 必须生成的文件
     (index-ts
      (path "[ComponentName]/index.ts")
      (description "导出文件：导出主组件及相关类型定义")
      (required t))  ;; 必须生成的文件
     (stories-tsx
      (path "[ComponentName]/[ComponentName].stories.tsx")
      (description "Storybook 文件：包含组件的基础用法示例；展示不同 props 组合的效果")
      (required t))) ;; 必须生成的文件

    ;; Props 设计要求
    (props-design
     (async-operations "所有异步操作（如数据获取、提交）都通过回调函数形式的 props 暴露")
     (typescript-types "使用 TypeScript 为所有 props 提供完整的类型定义")
     (semantic-naming "props 命名要符合业务语义")
     (default-values "必要时提供默认值"))

    ;; 样式要求
    (style-requirements
     (tailwind "优先使用 TailwindCSS 类名")
     (private-component "合理使用 private-component 组件")
     (antd "合理使用 Ant Design 组件")
     (responsive "遵循响应式设计原则")
     (spacing "注意组件间距和对齐"))

    ;; 代码规范
    (code-conventions
     (eslint "使用 ESLint 推荐配置")
     (pascal-case "组件和函数使用 PascalCase 命名")
     (camel-case "props 和变量使用 camelCase 命名")
     (comments "代码需要适当的注释说明"))

    ;; 输出要求
    (output-requirements
     (runnable "生成的代码应当可以直接运行")
     (typescript-types "包含必要的类型定义")
     (error-handling "包含基础的错误处理")
     (props-documentation "提供清晰的 props 文档"))
  ))