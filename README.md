# WMA Android Tools
## 1 - WMAAudioView

## WMAAudioView
Fornece um componente de áudio completo e pronto para executar faixas de áudio em MP3


### XML
```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:audio="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center">

    <br.com.wma.tools.widget.WMAAudioView
        android:id="@+id/avAudioView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="20dp"
        android:layout_marginRight="20dp"
        audio:progress="0"
        audio:elapsedTimeColor="#000000"
        audio:totalTimeColor="#000000"
        audio:backgroundContainer="@drawable/shape_audio"
        audio:audioTitle="Nome da Musica"
        audio:deleteTrack="true"
        audio:downloadTrack="true"
        audio:backToBegin="true"/>

</LinearLayout>
```

audio:elapsedTimeColor => Cor em hexadecimal
audio:totalTimeColor => Cor em hexadecimal
audio:backgroundContainer => Container de fundo do componente, pode ser um shape
audio:audioTitle => Título da Faixa de áudio
audio:deleteTrack => true ou false, faz a lixeira aparecer, precisa implementar o método onDelete
audio:downloadTrack => true ou false, aparece o botão de baixar faixa de áudio, necessário informar pasta de destino para o download
audio:backToBegin => true ou false, volta ao começo, quando o áudio termina.

### Java
```java
WMAAudioView wmaAudioView;
wmaAudioView = findViewById(R.id.avAudioView);
wmaAudioView.readyToPlayForStreamAsync(
        Activity,
        "URL STREM DA FAIXA DE AUDIO",
        new File("CAMINHO PARA SALVAR FICHEIRO")
);
wmaAudioView.setAudioTitle("Som Foda!");
wmaAudioView.addDeleteEvent(new OnDeleteEventListener() {
    @Override
    public void onDelete() {
        System.out.println("Captura o clique na lixeira!");
    }
});
```
