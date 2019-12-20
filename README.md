# thinkphp-filesystem
thinkphp6.0 filesystem,include Local Aliyun  Qiniu Qcloud

使用实例：

1# .ENV 文件设置默认驱动aliyun
[FILESYSTEM]
DRIVER=aliyun

2#Thinkphp6中使用示例
~~~
$file = request()->file();
if (empty($file) || !isset($file['img']) || empty($file['img'])) {
    return json_error('请上传图片');
}
try {
    validate(['img' => 'fileSize:10485670|fileExt:jpg,gif,jpeg,png|fileMime:image/jpeg,image/gif,image/png'])
        ->check($file);
    $path = \think\facade\Filesystem::putFile('images', $file['img']);
    return json_ok(['path' => $path]);
} catch (\think\exception\ValidateException $e) {
    return json_error($e->getMessage());
}
~~~
