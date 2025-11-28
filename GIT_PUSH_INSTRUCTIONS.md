# Instruksi Git Push

## File yang Sudah Diubah

File-file berikut sudah diubah untuk mendukung Jakarta EE 9+ dan Tomcat 11:

1. **pom.xml** - Update Java version ke 21
2. **gameoflife-web/pom.xml** - Update Spring ke 6.1.5, Jakarta servlet API
3. **gameoflife-web/src/main/webapp/WEB-INF/web.xml** - Migrasi ke Jakarta EE 6.0
4. **gameoflife-web/src/main/webapp/WEB-INF/gameoflife-servlet.xml** - Update Spring schema
5. **gameoflife-web/src/main/java/.../GameController.java** - Update import javax → jakarta
6. **gameoflife-web/src/test/java/.../*.java** - Update import javax → jakarta

## Langkah-langkah Git Push

### 1. Cek Status Git
```bash
cd /home/maxim/gawean/learn/devops/Project/GOL/gol
git status
```

### 2. Lihat Perubahan
```bash
# Lihat semua file yang diubah
git diff --name-only

# Lihat detail perubahan
git diff
```

### 3. Tambahkan File ke Staging
```bash
# Tambahkan semua file yang diubah
git add pom.xml
git add gameoflife-web/pom.xml
git add gameoflife-web/src/main/webapp/WEB-INF/web.xml
git add gameoflife-web/src/main/webapp/WEB-INF/gameoflife-servlet.xml
git add gameoflife-web/src/main/java/
git add gameoflife-web/src/test/java/

# ATAU tambahkan semua perubahan sekaligus
git add .
```

### 4. Commit Perubahan
```bash
git commit -m "Migrate to Jakarta EE 9+ and upgrade to Java 21

- Update pom.xml to use Java 21
- Upgrade Spring from 3.0.2 to 6.1.5 (Jakarta EE compatible)
- Migrate javax.servlet to jakarta.servlet
- Update web.xml to Jakarta EE 6.0
- Update Spring servlet configuration
- Fix compatibility with Tomcat 11"
```

### 5. Push ke GitHub
```bash
# Push ke branch master
git push origin master

# ATAU jika branch lain
git push origin <nama-branch>
```

## Command Lengkap (One-liner)

Jika ingin melakukan semua langkah sekaligus:

```bash
cd /home/maxim/gawean/learn/devops/Project/GOL/gol && \
git add . && \
git commit -m "Migrate to Jakarta EE 9+ and upgrade to Java 21

- Update pom.xml to use Java 21
- Upgrade Spring from 3.0.2 to 6.1.5 (Jakarta EE compatible)
- Migrate javax.servlet to jakarta.servlet
- Update web.xml to Jakarta EE 6.0
- Update Spring servlet configuration
- Fix compatibility with Tomcat 11" && \
git push origin master
```

## Catatan Penting

1. **Pastikan semua perubahan sudah benar** sebelum commit
2. **Jangan commit file**:
   - `target/` directory (sudah di .gitignore)
   - `pom.xml.bck` (backup file)
   - `.mvn/` directory
3. **Test build** sebelum push:
   ```bash
   mvn clean package -DskipTests
   ```

## Troubleshooting

### Jika ada conflict
```bash
# Pull perubahan terbaru
git pull origin master

# Resolve conflict, lalu
git add .
git commit -m "Resolve merge conflict"
git push origin master
```

### Jika lupa file
```bash
# Tambahkan file yang terlewat
git add <file-path>

# Update commit terakhir
git commit --amend --no-edit

# Force push (hati-hati!)
git push origin master --force
```

