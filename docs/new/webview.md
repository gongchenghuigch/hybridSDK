## Android新容器

1. loading（旧）

   ```
   export function loading({ text = '加载中', state, ...other }) {
       let params = { alertType: 'loading', text, state, ...other };
       let paramsToNative = { host: 'handlejs', path: 'showComponent', query: params };
       _nativeBridge(paramsToNative);
   }
   ```

2. toast（旧）

   ```
   export function toast({ text, state = 'prompt', ...other }) {
       let params = { alertType: 'toast', text, state, ...other };
       let paramsToNative = { host: 'handlejs', path: 'showComponent', query: params };
       _nativeBridge(paramsToNative);
   }
   ```

3. dialog（改）

   ```
   export function dialog(
       {
           title = '提示',
           content,
           btns = [{ text: '取消', color: '#000000' }, { text: '确定', color: '#ff552e' }],
           ...other
       },
       callback
   ) {
       let paramsToNative = {};
       let params = { title, content, btns, ...other };
       paramsToNative = { host: 'handlejs', path: 'CSTShowDialog', query: params };
       _nativeBridge(paramsToNative, callback);
   }
   ```

4. 跳转H5（改）

   ```
   export function pagetransWeb({ title, url, isDestoryBeforePage = 0, jumpParameter }, callback) {
       let paramsToNative = {};
       let params = {
           title,
           url,
           isDestoryBeforePage,
           jumpParameter
       };
       paramsToNative = { host: 'jumppage', path: 'loadWebPage', query: params };
       _nativeBridge(paramsToNative, callback);
   }
   ```

5. 跳转RN（旧）

   ```
   export function pagetransRN({ bundleId, isDestoryBeforePage = 0, jumpParameter }, callback) {
       let params = {
           bundleId,
           saveDataKey: 'jumpParamKey',
           callbackDataKey: 'callbackParamKey',
           isDestoryBeforePage,
           jumpParameter
       };
       let paramsToNative = { host: 'jumppage', path: 'RNPage', query: params };
       _nativeBridge(paramsToNative, callback);
   }
   ```

6. 跳转Native（旧）

   ```
   export function pagetransNative({
       pageType,
       page,
       tabIndex = 0,
       isDestoryBeforePage = 0,
       jumpParameter
   }) {
       let params = {
           desPage: page,
           subTabIndex: tabIndex,
           isDestoryBeforePage,
           jumpParameter
       };
       let paramsToNative = { host: 'jumppage', path: pageType, query: { data: params } };
       _nativeBridge(paramsToNative);
   }
   ```

7. photoSelect图片选择（旧）

   ```
   export function imgSelect({ maxSelectedNum, title, images, ...other }, callback) {
       let params = {
           data: {
               jumpParameter: {
                   maxSelectedNum,
                   title,
                   images,
                   ...other
               }
           }
       };
       let paramsToNative = { host: 'jumppage', path: 'photoSelect', query: params };
       _nativeBridge(paramsToNative, callback);
   }
   ```

8. 分享（旧）

   ```
   export function share(
       { imageType, imageBase64 = '', imageUrl, title, text, shareUrl, ...other },
       callback
   ) {
       let params = {
           cbDestory: true,
           data: {
               imageType,
               imageBase64,
               imageUrl,
               title,
               text,
               shareUrl,
               ...other
           }
       };
       let paramsToNative = { host: 'handlejs', path: 'newShare', query: params };
       _nativeBridge(paramsToNative, callback);
   }
   ```

9. 支付（直接跳转收银台）（新）

   ```
   export function gotoPay({ payOrderData, ...other }, callback) {
       const error = checker(arguments, [{ payOrderData: 'o' }], 'gotoPay');
       // 线上环境报错不调起 Native 的 API
       if (error === 'error') {
           return error;
       }
       let paramsToNative = {
           host: 'handlejs',
           path: 'CSTNativeFunctionPay',
           query: { payOrderData, ...other }
       };
       _nativeBridge(paramsToNative, callback);
   }
   ```

10. 获取地理位置（新）

    ```
    export function getLocation(callback) {
        let paramsToNative = { host: 'handlejs', path: 'CSTNativeFunctionCity ', query: {} };
        _nativeBridge(paramsToNative, callback);
    }
    ```

11. statistic埋点（旧）

    ```
    export function setWeblog({ eventId, attributes }) {
        let paramsToNative = {
            host: 'handlejs',
            path: 'statistic ',
            query: { data: [{ eventId, attributes }] }
        };
        _nativeBridge(paramsToNative);
    }
    ```

12. 关闭当前页（旧）

    ```
    export function closeCurrentPage() {
        let paramsToNative = {
            host: 'handlejs',
            path: 'closeCurrentPage',
            query: {}
        };
        _nativeBridge(paramsToNative);
    }
    ```

13. 图片、视频上传（旧）

    ```
    export function imgUpload(
        { maxNum, title = '图片选择', isNeedTakingPic = 0, selectDesc, data, videoNum, ...other },
        callback
    ) {
        let params = {
            maxNum,
            title,
            isNeedTakingPic,
            selectDesc,
            data,
            videoNum,
            ...other
        };
        let paramsToNative = {
            host: 'handlejs',
            path: 'picselect',
            query: params
        };
        _nativeBridge(paramsToNative, callback);
    }
    ```

14. 设置页面标题（新）

    ```
    export function setTitle(title = '') {
        let paramsToNative = {
            host: 'handlejs',
            path: 'setTitle',
            query: { title }
        };
        _nativeBridge(paramsToNative);
    }
    ```

15. 配置webview下拉刷新上拉加载（新）

    ```
    export function pullRefresh(
        { pullDownRefresh = false, pullUpLoadMore = false, ...other },
        callback
    ) {
        let params = {
            pullDownRefresh,
            pullUpLoadMore,
            ...other
        };
        let paramsToNative = {
            host: 'handlejs',
            path: 'pullRefresh',
            query: params
        };
        _nativeBridge(paramsToNative, callback);
    }
    ```

16. 结束加载动画（旧）

    ```
    export function endAnimate({ endMode }) {
        let paramsToNative = {
            host: 'handlejs',
            path: 'pullendnotify',
            query: { endMode }
        };
        _nativeBridge(paramsToNative);
    }
    ```

17. 事件监听（新）

    ```
    export function deviceEvent({ type = 'goback', ...other }, callback) {
        let params = {
            type,
            ...other
        };
        let paramsToNative = {
            host: 'handlejs',
            path: 'deviceEvent',
            query: params
        };
        _nativeBridge(paramsToNative, callback);
    }
    ```

18. 网络请求（旧）

    ```
    export function nativeRequest(
        {
            url,
            param,
            method,
            header = {
                'X-Requested-With': 'XMLHttpRequest',
                Accept: '*/*',
                'Content-Type': 'application/json; charset=utf-8'
            },
            network_id,
            ...other
        },
        callback
    ) {
        url = url.replace(/^http:\/\/|^HTTP:\/\/|^\/\//, function() {
            return location.protocol + '//';
        });
        let params = {
            url,
            param,
            method,
            header,
            network_id,
            ...other
        };
        let paramsToNative = {
            host: 'handlejs',
            path: 'nativeRequest',
            query: params
        };
        _nativeBridge(paramsToNative, callback);
    }
    ```

19. 获取用户信息（新）

20. 获取设备信息（新）

未完待续...

