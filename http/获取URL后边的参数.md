# 获取URL后边的参数
``` Java
export const getQueryVariable = variable => {
  const searchParams = new URLSearchParams(window.location.search.substring(1))
  return searchParams.get(variable)
}
```
