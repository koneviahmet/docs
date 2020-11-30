```python
import os
```



# terminal kod tetikleme

aşağıdaki gibi osu kullanırsak terminalden komut tetiklettirebiliyoruz.

> from os import system as komut

```python
komut("editor")
```






```python
# işletim sisteminin adını verir
# posix => linux
# nt => windoes
os.name
```




    'posix'




```python
# / => linux
# \\ => windows
os.sep
```




    '/'




```python
# bulunduğu dizininin yolunu verir.
os.getcwd()
```




    '/home/ahmet/Masaüstü/python/jupyterNotlar'




```python
# başka bir dizine geçmesine izin verir
# os.chdir('/usr/bin/')
```


```python
# dizin içinde bulunan dosta ve klasörleri liseleter
os.listdir()
```




    ['os.ipynb', '.ipynb_checkpoints']




```python
# mevcut dizinde liseleteme yapalım 

```


```python
mevcut_dizin = os.getcwd()
os.listdir(mevcut_dizin)
```




    ['os.ipynb', '.ipynb_checkpoints']




```python
# başa bir dizinde listeleme yapalım
os.listdir('/var/www')
```




    ['html']




```python
# sadece windowsta çalışır
# varsayılan proğramda dosyayı çalıştırır
# os.startfile('deneme.txt')
```


```python
# yeni dizi oluşturur
# os.mkdir('yenidizin')
# os.mkdirs('dizin yolu') => yolu verillen tüm dizinleri dosya olarak oluşturur.
```


```python
# os.rename(kullanilan_isim, yeni_isim) => dosa ismi değiştirmek için kulanılır
# os.replace() aynı işi apar
```


```python
#os.remove('dosya adı') => siler
#os.rmdir() => içi boş dosyayı siler
```


```python
# os.rmdir('anadizin')
# os.rmdir(r'anadizin/dizin1')
# os.rmdir(r'anadizin/dizin1/dizin2/dizin3')
```


```python
# dosya hakkında bilgi almamızı sağlar
# dosya = os.stat('dosya_adı')
```


```python

# dir(dosya) bilgi almak için kullanılır
"""
st_atime
dosyaya en son erişilme tarihi

st_ctime
dosyanın oluşturulma tarihi (Windows’ta)

st_mtime
dosyanın son değiştirilme tarihi

st_size
dosyanın boyutu
"""
```




    '\nst_atime\ndosyaya en son erişilme tarihi\n\nst_ctime\ndosyanın oluşturulma tarihi (Windows’ta)\n\nst_mtime\ndosyanın son değiştirilme tarihi\n\nst_size\ndosyanın boyutu\n'




```python
# örnek
# dosya = os.stat('dosya_adı')
# dosya.st_size
```


```python
# terminale komut girmemizi sağlar
os.system('atom')
```




    0




```python
# 12 byt tan oluşan rasgele bir sayı oluşturur.
os.urandom(12)
```




    b'\xf9/X(\xc0:r\xa3\xe0-\xce\x0b'




```python
# işletim sisteminin çevre değişlenleri hakkında bilgi atoplarızs
os.environ

```




    environ{'SHELL': '/bin/bash',
            'SESSION_MANAGER': 'local/ahmet:@/tmp/.ICE-unix/1658,unix/ahmet:/tmp/.ICE-unix/1658',
            'QT_ACCESSIBILITY': '1',
            'COLORTERM': 'truecolor',
            'XDG_CONFIG_DIRS': '/etc/xdg/xdg-ubuntu:/etc/xdg',
            'XDG_MENU_PREFIX': 'gnome-',
            'GNOME_DESKTOP_SESSION_ID': 'this-is-deprecated',
            'GTK_IM_MODULE': 'ibus',
            'QT4_IM_MODULE': 'ibus',
            'JAVA_HOME': '/usr/lib/jvm/java-11-openjdk-amd64',
            'GNOME_SHELL_SESSION_MODE': 'ubuntu',
            'SSH_AUTH_SOCK': '/run/user/1000/keyring/ssh',
            'GRADLE_HOME': '/opt/gradle/gradle-6.4',
            'XMODIFIERS': '@im=ibus',
            'DESKTOP_SESSION': 'ubuntu',
            'SSH_AGENT_PID': '1536',
            'GTK_MODULES': 'gail:atk-bridge',
            'PWD': '/home/ahmet',
            'LOGNAME': 'ahmet',
            'XDG_SESSION_DESKTOP': 'ubuntu',
            'XDG_SESSION_TYPE': 'x11',
            'GPG_AGENT_INFO': '/run/user/1000/gnupg/S.gpg-agent:0:1',
            'XAUTHORITY': '/run/user/1000/gdm/Xauthority',
            'GJS_DEBUG_TOPICS': 'JS ERROR;JS LOG',
            'WINDOWPATH': '2',
            'HOME': '/home/ahmet',
            'USERNAME': 'ahmet',
            'IM_CONFIG_PHASE': '1',
            'LANG': 'tr_TR.UTF-8',
            'LS_COLORS': 'rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:',
            'XDG_CURRENT_DESKTOP': 'ubuntu:GNOME',
            'VTE_VERSION': '6001',
            'GNOME_TERMINAL_SCREEN': '/org/gnome/Terminal/screen/f4eec2c2_b080_4918_9634_812bd8904b96',
            'INVOCATION_ID': 'ef118a5db04f4f119123b9bd888874da',
            'MANAGERPID': '1275',
            'CLUTTER_IM_MODULE': 'ibus',
            'GJS_DEBUG_OUTPUT': 'stderr',
            'LESSCLOSE': '/usr/bin/lesspipe %s %s',
            'XDG_SESSION_CLASS': 'user',
            'ANDROID_HOME': '/home/ahmet/Android/Sdk',
            'TERM': 'xterm-color',
            'LESSOPEN': '| /usr/bin/lesspipe %s',
            'USER': 'ahmet',
            'GNOME_TERMINAL_SERVICE': ':1.136',
            'DISPLAY': ':0',
            'SHLVL': '1',
            'ANDROID_SDK_ROOT': '/home/ahmet/Android/Sdk',
            'QT_IM_MODULE': 'ibus',
            'XDG_RUNTIME_DIR': '/run/user/1000',
            'JOURNAL_STREAM': '9:38525',
            'XDG_DATA_DIRS': '/usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop',
            'PATH': '/home/ahmet/.local/bin:/opt/gradle/gradle-6.4/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/ahmet/Android/Sdk/tools:/home/ahmet/Android/Sdk/platform-tools:/home/ahmet/Android/Sdk/emulator:/home/ahmet/Android/Sdk/tools:/home/ahmet/Android/Sdk/tools/bin:/home/ahmet/Android/Sdk/platform-tools',
            'GDMSESSION': 'ubuntu',
            'DBUS_SESSION_BUS_ADDRESS': 'unix:path=/run/user/1000/bus',
            '_': '/home/ahmet/.local/bin/jupyter',
            'KERNEL_LAUNCH_TIMEOUT': '40',
            'JPY_PARENT_PID': '5419',
            'CLICOLOR': '1',
            'PAGER': 'cat',
            'GIT_PAGER': 'cat',
            'MPLBACKEND': 'module://ipykernel.pylab.backend_inline'}




```python
# dosyanın tam yolunu verir
os.path.abspath('falanca.txt')
```




    '/home/ahmet/Masaüstü/python/jupyterNotlar/falanca.txt'




```python
# dosya yolunu verir
os.path.dirname('/home/istihza/Desktop/falanca.txt')
```




    '/home/istihza/Desktop'




```python
#  bir dosya veya dizinin varolup olmadığını kontrol eder:
os.path.exists('/home/istihza/Desktop/falanca.txt')
```




    False




```python
# kullanıcıya ait dizinin adını verir
os.path.expanduser('~')
```




    '/home/ahmet'




```python
# parametre olarak verilen öğenin bir dizin olup olmadığını sorgular
os.path.isdir('/home/ahmet')
```




    True




```python
# dosya olup olmadığını sorgular
os.path.isfile('/home/istihza/falance.txt')
```




    False




```python
# işletim sistemine uygun dizin oluşturur.
os.path.join('dizin1', 'dizin2', 'dizin3')
# win => 'dizin1\\dizin2\\dizin3'
# linux => 'dizin1/dizin2/dizin3'
```




    'dizin1/dizin2/dizin3'




```python
os.path.split('/home/istihza/Desktop')
#son kısmını baş kısmından ayırır:
```




    ('/home/istihza', 'Desktop')




```python
# splitext() fonksiyonu dosya adı ile uzantısını birbirinden ayırmak için kullanılır:
os.path.splitext('falanca.txt')
```




    ('falanca', '.txt')




```python

```
