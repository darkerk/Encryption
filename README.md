
// 加密文件事例

    NSString *docDir = [NSHomeDirectory() stringByAppendingPathComponent:@"Documents"];
    NSString *toPath = [docDir stringByAppendingPathComponent:@"database.db"];
    
    NSFileManager *fileManager = [NSFileManager defaultManager];
    if (![fileManager fileExistsAtPath:toPath]) {
        NSString *inPath = [[[NSBundle mainBundle] resourcePath] stringByAppendingPathComponent:@"database.db"];

        NSError  *error = nil;
        if (![[NSFileManager defaultManager] AESEncryptFile:inPath toFile:toPath usingPassphrase:@"password" error:&error])
        {
            NSLog(@"加密文件失败：%@", [[error userInfo] objectForKey:AESEncryptionErrorDescriptionKey]);
        }
/**************
        if (![[NSFileManager defaultManager] AESDecryptFile:inPath toFile:toPath usingPassphrase:@"password" error:&error])
        {
            NSLog(@"解密文件失败：%@", [[error userInfo] objectForKey:AESEncryptionErrorDescriptionKey]);
        }
 ***************/
    }
