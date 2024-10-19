![image](https://github.com/user-attachments/assets/8b7ff85b-fc08-4307-b3fe-e005b84fef9f)

## <a name="commit"></a> Pedoman Commit Message

Berikut adalah command Git yang disesuaikan dengan alur diagram diatas:

### **Branch Utama (`main`)**

  * Pindah ke Branch Utama:
   
   ```
   git checkout main
   ```

### **Branch Fitur (`feature/xyz`)**

  * Buat branch fitur baru (berdasarkan `develop`):

   ```
   git checkout develop
   git checkout -b feature/xyz
   ```

  * Commit perubahan di branch fitur:

   ```
   git add .
   git commit -m "Tambah fitur baru xyz"
   ```
   
  * Gabungkan branch fitur ke `develop` setelah fitur selesai:

   ```
   git checkout develop
   git merge feature/xyz
   git branch -d feature/xyz
   ```

### **Branch Develop (`develop`)**

  * Gabungkan develop ke branch release ketika fitur siap diuji:

   ```
   git checkout release
   git merge develop
   ```

### **Branch Rilis (`release`)**

  * Buat branch release (berdasarkan `develop`):

   ```
   git checkout develop
   git checkout -b release/v1.0
   ```

  * Gabungkan branch release ke `main` setelah testing selesai:

   ```
   git checkout main
   git merge release/v1.0
   ```
  * Tag versi rilis:

   ```
   git tag v1.0
   git push --tags
   ```

### **Branch Hotfix (`hotfix`)**

  * Buat branch hotfix untuk memperbaiki masalah langsung di brach `main`:
    
    ```
    git checkout main
    git checkout -b hotfix/v1.1
    ```
  
  * Commit perubahan hotfix:

    ```
    git add .
    git commit -m "Perbaikan untuk masalah xyz"
    ```
    
  * Gabungkan hotfix ke `main` dan `develop` agar perbaikan tersedia di kedua branch:

    ```
    git checkout main
    git merge hotfix/v1.1
    git checkout develop
    git merge hotfix/v1.1
    git branch -d hotfix/v1.1
    ```

Command di atas akan membantu memastikan alur pengembangan yang rapi dan terstruktur sesuai dengan diagram branching Git Diatas
