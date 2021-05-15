<h1 align="center"> Android-Live-Templates </h1>

<div align="center">
  <img src="https://awesome.re/badge.svg" alt="Awesome Badge"/>
  <img src="https://img.shields.io/static/v1?label=%F0%9F%8C%9F&message=If%20Useful&style=style=flat&color=BC4E99" alt="Star Badge"/>
  <img src="https://img.shields.io/badge/Follow-%40code.fun-red?style=social&logo=instagram" alt="Instagram Badge"/>
</div>
<h5 align="center"> <i> A curated list of Android Live Templates </i> </h5>
<img alt="Poster" src="assets/logo_two.png"> </img>
<div align="center">
  <img src="https://badgen.net/github/stars/agamkoradiya/Android-Live-Templates" alt="Star Badge"/>
  <img src="https://badgen.net/github/forks/agamkoradiya/Android-Live-Templates" alt="Fork Badge"/>
  <img src="https://badgen.net/github/issues/agamkoradiya/Android-Live-Templates" alt="Issues Badge"/>
  <img src="https://badgen.net/github/prs/agamkoradiya/Android-Live-Templates" alt="PR Badge"/>
  <img src="https://badgen.net/github/contributors/agamkoradiya/Android-Live-Templates" alt="Contributors Badge"/>
  <img src="https://badgen.net/github/license/agamkoradiya/Android-Live-Templates" alt="License Badge"/>
</div>

# Content
  - [What is live template? 😮](#what-is-live-template-)
  - [Demo 💻](#demo-)
  - [How to *import all live templates* in 1 minute? 💥](#how-to-import-all-live-templates-in-1-minute-)
  - [CheatSheet for this repository 📄](#cheatsheet-)
      - [Adapter](#-adapter)
          - [adapter list](#adapter-list)
          - [adapter normal](#adapter-normal)
      - [View binding](#-view-binding)
          - [binding activity](#binding-activity)
          - [binding fragment](#binding-fragment)
      - [Retrofit library](#-retrofit-library)
          - [retofit instance](#retrofit-instance)
      - [Room database](#-room-database)
          - [room db](#room-db)
          - [room db with singleton](#room-db-with-singleton)
          - [room dao](#room-dao)
          - [room converter for list of string](#room-converter-for-list-of-string)
          - [room converter for date](#room-converter-for-date)
          - [room converter for bitmap](#room-converter-for-bitmap)
      - [Dependency Injection](#-dependency-injection)
          - [di hilt app](#di-hilt-app)
          - [di retrofit module](#di-retrofit-module)
          - [di room module](#di-room-module)
      - [Drawable](#-drawable)
          - [shape bubble](#shape-bubble)
          - [shape halfcircle](#shape-halfcircle)
          - [shape line](#shape-line)
          - [shape oval](#shape-oval)
          - [shape ractangle](#shape-ractangle)
          - [shape ring](#shape-ring)
          - [shape round](#shape-round)
          - [state list](#state-list)
      - [XML](#-xml)
          - [center_horizontal](#center-horizontal)
          - [center_horizontal_parent](#center-horizontal-parent)
          - [center_parent](#center-parent)
          - [center_vartical](#center-vartical)
          - [center_vartical_parent](#center-vartical-parent)
          - [xml_menu](#xml-menu)
      - [Util](#-util)
          - [util resource](#util-resource)
          - [util toast](#util-toast)
      - [Gradle dependency](#-gradle-dependency)
  - [How to create your own live templates? 💡](#how-to-create-your-own-live-templates-)
  - [Suggest me! ✒️](#suggest-me)
  - [Contribute ❤️](#contribute)

---

## What is live template? 😮
<samp> Live Templates are code snippets that you can insert into your code by typing their abbreviation and pressing tab.
By using them, you can quickly and intelligently add frequently used code patterns and constructs to your code, letting the IDE do the tedious work for you. </samp>

## Demo 💻
<img alt="How to import all live templates" src="assets/demoFirst.gif"> </img>
<img alt="How to import all live templates" src="assets/demoSecond.gif"> </img>
<br>

## How to import all live templates in 1 minute? 💥
1. Download AndroidLiveTemplates.zip file
2. Then follow below video tutorial
<br>
<img alt="How to import all live templates" src="assets/howToImport.gif"> </img>
<br>

## CheatSheet 📄

### 📌 Adapter
<br>

<div name="adapter-list">

>  <samp> adapter list </samp>
  
```kotlin 
class $FILE_NAME$ : androidx.recyclerview.widget.ListAdapter<$TYPE$, $FILE_NAME$.$HOLDER_NAME$ViewHolder>(DiffCallback()) {

    override fun onCreateViewHolder(parent: android.view.ViewGroup, viewType: Int): $HOLDER_NAME$ViewHolder {
        val binding =
            $BINDING$.inflate(
                android.view.LayoutInflater.from(parent.context),
                parent,
                false
            )
        return $HOLDER_NAME$ViewHolder(binding)
    }

    override fun onBindViewHolder(holder: $HOLDER_NAME$ViewHolder, position: Int) {
        val currentItem = getItem(position)
    }

    inner class $HOLDER_NAME$ViewHolder(private val binding: $BINDING$) :
        androidx.recyclerview.widget.RecyclerView.ViewHolder(binding.root) {}

    class DiffCallback : androidx.recyclerview.widget.DiffUtil.ItemCallback<$TYPE$>() {
        override fun areItemsTheSame(oldItem: $TYPE$, newItem: $TYPE$) =
            oldItem.id == newItem.id

        override fun areContentsTheSame(oldItem: $TYPE$, newItem: $TYPE$) =
            oldItem == newItem
    }
}
```
</div>
<br>

<div name="adapter-normal">

>  <samp> adapter normal </samp>
  
```kotlin
  class $FILE_NAME$ : androidx.recyclerview.widget.RecyclerView.Adapter<$FILE_NAME$.MyViewHolder>() {

    class MyViewHolder(itemView: android.view.View) : androidx.recyclerview.widget.RecyclerView.ViewHolder(itemView) {}

    override fun onCreateViewHolder(parent: android.view.ViewGroup, viewType: Int): MyViewHolder {
        return MyViewHolder(
            android.view.LayoutInflater.from(parent.context).inflate(R.layout.$LAYOUT$, parent, false)
        )
    }

    override fun getItemCount(): Int {
        TODO("Not yet implemented")
    }

    override fun onBindViewHolder(holder: MyViewHolder, position: Int) {
        TODO("Not yet implemented")
    }
}
```
</div>
<br>

### 📌 View Binding
<br>

<div name="binding-activity">

>  <samp> binding activity </samp>

```kotlin
class $FILE_NAME$ : androidx.appcompat.app.AppCompatActivity() {

    private lateinit var binding: $BINDING_LAYOUT$

    override fun onCreate(savedInstanceState: android.os.Bundle?) {
        super.onCreate(savedInstanceState)
        binding = $BINDING_LAYOUT$.inflate(layoutInflater)
        val view = binding.root
        setContentView(view)
    }
}
```
</div>
<br>

<div name="binding-fragment">

>  <samp> binding fragment </samp>

```kotlin
class $FILE_NAME$ : androidx.fragment.app.Fragment() {

    private var _binding: $BINDING_LAYOUT$? = null
    private val binding get() = _binding!!

    override fun onCreateView(
        inflater: android.view.LayoutInflater,
        container: android.view.ViewGroup?,
        savedInstanceState: android.os.Bundle?
    ): android.view.View {
        _binding = $BINDING_LAYOUT$.inflate(inflater, container, false)
        return binding.root
    }

    override fun onDestroyView() {
        super.onDestroyView()
        _binding = null
    }
}
```
</div>
<br>

### 📌 Retrofit Library
<br>

<div name="retrofit-instance">

>  <samp> retrofit instance </samp>

```kotlin
class $FILE_NAME$ {

    companion object {

        private val retrofit by lazy {
            val logging = okhttp3.logging.HttpLoggingInterceptor()
            logging.setLevel(okhttp3.logging.HttpLoggingInterceptor.Level.$TYPE$)
            val client = okhttp3.OkHttpClient.Builder()
                .addInterceptor(logging)
                .build()
            retrofit2.Retrofit.Builder()
                .baseUrl($BASE_URL$)
                .addConverterFactory(retrofit2.converter.gson.GsonConverterFactory.create())
                .client(client)
                .build()
        }

        val api by lazy {
            retrofit.create($API_NAME$::class.java)
        }
    }
    
}
```
</div>
<br>

### 📌 Room Database
<br>

<div name="room-db">

>  <samp> room db </samp>

```kotlin
@androidx.room.Database(
    entities = [$TABLE_NAME$::class],
    version = 1,
    exportSchema = false
)
@androidx.room.TypeConverters($CONVERTER_NAME$::class)
abstract class $FILE_NAME$ : androidx.room.RoomDatabase() {

    abstract fun $DAO_NAME$(): $DAO_TYPE$
    
}
```
</div>
<br>

<div name="room-db-with-singleton">

>  <samp> room db with singleton </samp>

```kotlin
@androidx.room.Database(
    entities = [$TABLE_NAME$::class],
    version = 1,
    exportSchema = false
)
@androidx.room.TypeConverters($CONVERTER_NAME$::class)
abstract class $FILE_NAME$ : androidx.room.RoomDatabase() {

    abstract fun $DAO_NAME$(): $DAO_TYPE$

    companion object {
        @Volatile
        private var INSTANCE: $FILE_NAME$? = null
        private val LOCK = Any()

        fun getDatabase(context: android.content.Context): $FILE_NAME$ =
            INSTANCE ?: synchronized(LOCK) {
                INSTANCE
                    ?: buildDatabase(context).also { INSTANCE = it }
            }

        private fun buildDatabase(context: android.content.Context) =
            androidx.room.Room.databaseBuilder(
                context.applicationContext,
                $FILE_NAME$::class.java, "$DB_NAME$.db"
            ).build()
    }
}
```
</div>
<br>

<div name="room-dao">

>  <samp> room dao </samp>

```kotlin
import androidx.room.*

@Dao
interface $FILE_NAME$ {

    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun insert$TABLE_NAME$($VAR_NAME$: $TABLE_NAME$)
    
    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun insertAll$TABLE_NAME$(vararg $VAR_NAME$s: $TABLE_NAME$)

    @Update
    suspend fun update($VAR_NAME$: $TABLE_NAME$)

    @Delete
    suspend fun delete($VAR_NAME$: $TABLE_NAME$)

    @Query("SELECT * FROM $VAR_NAME$")
    fun getAll$TABLE_NAME$(): List<$TABLE_NAME$>

}
```
</div>
<br>

<div name="room-converter-for-list-of-string">

>  <samp> room converter for list of string </samp>

```kotlin
// List<String> <-> String
@androidx.room.TypeConverter
fun fromList(list: List<String>): String {
    return com.google.gson.Gson().toJson(list)
}

@androidx.room.TypeConverter
fun toList(string: String): List<String> {
    return com.google.gson.Gson().fromJson(string, object : com.google.gson.reflect.TypeToken<List<String>>() {}.type)
}
```
</div>
<br>

<div name="room-converter-for-date">

>  <samp> room converter for date </samp>

```kotlin
// Date <-> Long
@androidx.room.TypeConverter
fun fromTimestamp(value: Long?): java.util.Date? {
    return value?.let { java.util.Date(it) }
}

@androidx.room.TypeConverter
fun dateToTimestamp(date: java.util.Date?): Long? {
    return date?.time?.toLong()
}
```
</div>
<br>

<div name="room-converter-for-bitmap">

>  <samp> room converter for bitmap </samp>

```kotlin
// Bitmap <-> ByteArray
@androidx.room.TypeConverter
fun fromBitmap(bitmap: android.graphics.Bitmap): ByteArray {
    val outputStream = java.io.ByteArrayOutputStream()
    bitmap.compress(android.graphics.Bitmap.CompressFormat.PNG, 100, outputStream)
    return outputStream.toByteArray()
}

@androidx.room.TypeConverter
fun toBitmap(byteArray: ByteArray): android.graphics.Bitmap {
    return android.graphics.BitmapFactory.decodeByteArray(byteArray, 0, byteArray.size)
}
```
</div>
<br>

### 📌 Dependency Injection
<br>

<div name="di-hilt-app">

>  <samp> di hilt app </samp>

```kotlin
@dagger.hilt.android.HiltAndroidApp
class $FILE_NAME$ : android.app.Application() {
}
```
</div>
<br>

<div name="di-retrofit-module">

>  <samp> di retrofit module </samp>

```kotlin
@javax.inject.Singleton
@dagger.Provides
fun provideRetrofit(): retrofit2.Retrofit =
    retrofit2.Retrofit.Builder()
        .baseUrl($BASE_URL$)
        .addConverterFactory(retrofit2.converter.gson.GsonConverterFactory.create())
        .build()

@javax.inject.Singleton
@dagger.Provides
fun provide$API_NAME$(retrofit: retrofit2.Retrofit): $API$ =
    retrofit.create($API$::class.java)
```
</div>
<br>

<div name="di-room-module">

>  <samp> di room module </samp>

```kotlin
@javax.inject.Singleton
@dagger.Provides
fun provideDatabase(
    @dagger.hilt.android.qualifiers.ApplicationContext context: android.content.Context
) = androidx.room.Room.databaseBuilder(
    context,
    $DATABASE_CLASS$::class.java,
    "$DATABASE_NAME$"
).build()

@javax.inject.Singleton
@dagger.Provides
fun provideDao(database: $DATABASE_CLASS$) = database.$METHOD$
```
</div>
<br>

### 📌 Drawable
<br>

<div name="shape-bubble">

>  <samp> shape bubble </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">

    <corners
        android:bottomRightRadius="10dp"
        android:radius="40dp" />

    <stroke
        android:width="1dp"
        android:color="@color/$STROKE_COLOR$" />

    <size
        android:width="50dp"
        android:height="50dp" />
        
    <solid android:color="@color/$SOLID_COLOR$" />

</shape>
```
</div>
<br>

<div name="shape-halfcircle">

>  <samp> shape halfcircle </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">

    <corners
        android:topLeftRadius="60dp"
        android:topRightRadius="60dp" />

    <size
        android:width="120dp"
        android:height="60dp" />

    <solid android:color="@color/$SOLID_COLOR$" />

</shape>
```
</div>
<br>

<div name="shape-line">

>  <samp> shape line </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="line">

    <stroke
        android:width="3dp"
        android:color="@color/$STROKE_COLOR$" />

    <size android:height="1dp" />

</shape>
```
</div>
<br>

<div name="shape-oval">

>  <samp> shape oval </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="oval">

    <stroke
        android:width="3dp"
        android:color="@color/$STROKE_COLOR$" />

    <solid android:color="@color/$SOLID_COLOR$" />

</shape>
```
</div>
<br>

<div name="shape-ractangle">

>  <samp> shape ractangle </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">

    <corners android:radius="10dp" />

    <stroke
        android:width="3dp"
        android:color="@color/$STROKE_COLOR$" />

    <solid android:color="@color/$SOLID_COLOR$" />

</shape>
```
</div>
<br>

<div name="shape-ring">

>  <samp> shape ring </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="ring"
    android:thickness="5dp"
    android:useLevel="false">
    
    <solid android:color="@color/$SOLID_COLOR$" />

</shape>
```
</div>
<br>

<div name="shape-round">

>  <samp> shape round </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>

<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:innerRadius="0dp"
    android:shape="ring"
    android:thickness="100dp"
    android:useLevel="false">

    <solid android:color="@color/$SOLID_COLOR$" />

</shape>
```
</div>
<br>

<div name="state-list">

>  <samp> state list </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>

<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@drawable/$DRAWABLE1$" android:state_pressed="true" /> <!-- pressed -->
    <item android:drawable="@drawable/$DRAWABLE2$" android:state_focused="true" /> <!-- focused -->
    <item android:drawable="@drawable/$DRAWABLE3$" android:state_hovered="true" /> <!-- hovered -->
    <item android:drawable="@drawable/$DRAWABLE4$" android:state_selected="true" /> <!-- selected -->
    <item android:drawable="@drawable/$DRAWABLE5$" android:state_checkable="true" /> <!-- checkable -->
    <item android:drawable="@drawable/$DRAWABLE6$" android:state_checked="true" /> <!-- checked -->
    <item android:drawable="@drawable/$DRAWABLE7$" android:state_enabled="true" /> <!-- enabled -->
    <item android:drawable="@drawable/$DRAWABLE8$" android:state_activated="true" /> <!-- activated -->
    <item android:drawable="@drawable/$DRAWABLE9$" android:state_window_focused="true" /> <!-- window_focused -->
    <item android:drawable="@drawable/$DRAWABLE$" /> <!-- default -->
</selector>
```
</div>
<br>

### 📌 XML
<br>

<div name="center-horizontal">

>  <samp> center_horizontal </samp>

```kotlin
        app:layout_constraintEnd_toStartOf="@+id/$VIEWIDSTART$"
        app:layout_constraintStart_toEndOf="@+id/$VIEWIDEND$"
```
</div>
<br>

<div name="center-horizontal-parent">

>  <samp> center_horizontal_parent </samp>

```kotlin
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
```
</div>
<br>

<div name="center-parent">

>  <samp> center_parent </samp>

```kotlin
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent"
```
</div>
<br>

<div name="center-vartical">

>  <samp> center_vartical </samp>

```kotlin
        app:layout_constraintBottom_toTopOf="@+id/$VIEWIDTOP$"
        app:layout_constraintTop_toBottomOf="@+id/$VIEWIDBOTTOM$"
```
</div>
<br>

<div name="center-vartical-parent">

>  <samp> center_vartical_parent </samp>

```kotlin
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintTop_toTopOf="parent"
```
</div>
<br>

<div name="xml-menu">

>  <samp> xml_menu </samp>

```kotlin
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <item
        android:id="@+id/menu_$ID1$"
        android:icon="@drawable/$ICON1$"
        android:title="@string/$TITLE1$"
        app:showAsAction="$ACTION1$" />

    <item
        android:id="@+id/menu_$ID2$"
        android:icon="@drawable/$ICON2$"
        android:title="@string/$TITLE2$"
        app:showAsAction="$ACTION2$" />
        
    <item
        android:id="@+id/menu_$ID3$"
        android:icon="@drawable/$ICON3$"
        android:title="@string/$TITLE3$"
        app:showAsAction="$ACTION3$" />
        
        <item
        android:id="@+id/menu_$ID4$"
        android:icon="@drawable/$ICON4$"
        android:title="@string/$TITLE4$"
        app:showAsAction="$ACTION4$" />
        
    <item
        android:id="@+id/menu_$ID5$"
        android:icon="@drawable/$ICON5$"
        android:title="@string/$TITLE5$"
        app:showAsAction="$ACTION5$" />
        
</menu>
```
</div>
<br>

### 📌 Util
<br>

<div name="util-resource">

>  <samp> util resource </samp>

```kotlin
sealed class Resource<T>(val data: T?, val message: String?) {
    class Success<T>(data: T) : Resource<T>(data, null)
    class Error<T>(message: String) : Resource<T>(null, message)
}
```
</div>
<br>

<div name="util-toast">

>  <samp> util toast </samp>

```kotlin
fun android.content.Context.toast(message: CharSequence) =
    android.widget.Toast.makeText(this, message, android.widget.Toast.$LENGTH$).show()
```
</div>
<br>

### 📌 Gradle dependency
<br>

<div name="coil-depen">

>  <samp> coil depen </samp>

```kotlin
// Coil Image Loading Library
    implementation "io.coil-kt:coil:1.2.1"
```
</div>
<br>

<div name="coroutines-depen">

>  <samp> coroutines depen </samp>

```kotlin
// Coroutines Dependency
    implementation "org.jetbrains.kotlinx:kotlinx-coroutines-core:1.4.3"
    implementation "org.jetbrains.kotlinx:kotlinx-coroutines-android:1.4.3"
```
</div>
<br>

<div name="data-binding">

>  <samp> data binding </samp>

```kotlin
apply plugin: 'kotlin-kapt'

buildFeatures {
    dataBinding true
}
```
</div>
<br>

<div name="datastore-depen">

>  <samp> datastore depen </samp>

```kotlin
// Data store
// Typed DataStore (Typed API surface, such as Proto)
    implementation "androidx.datastore:datastore:1.0.0-beta01"
// Preferences DataStore (SharedPreferences like APIs)
    implementation "androidx.datastore:datastore-preferences:1.0.0-beta01"
```
</div>
<br>

<div name="easy-permission-depen">

>  <samp> easy permission depen </samp>

```kotlin
// Easy permission library
    implementation 'com.vmadalin:easypermissions-ktx:1.0.0'
```
</div>
<br>

<div name="glide-depen">

>  <samp> glide depen </samp>

```kotlin
// Glide Image Loading Library
    implementation 'com.github.bumptech.glide:glide:4.12.0'
    annotationProcessor 'com.github.bumptech.glide:compiler:4.12.0'
```
</div>
<br>

<div name="hilt-classpath">

>  <samp> hilt classpath </samp>

```kotlin
classpath "com.google.dagger:hilt-android-gradle-plugin:2.35"
```
</div>
<br>

<div name="hilt depen">

>  <samp> hilt depen </samp>

```kotlin
// Hilt Dependency Injection
    implementation "com.google.dagger:hilt-android:2.35"
    kapt "com.google.dagger:hilt-compiler:2.35"
```
</div>
<br>

<div name="hilt-plugin">

>  <samp> hilt plugin </samp>

```kotlin
id 'kotlin-kapt'
id 'dagger.hilt.android.plugin'
```
</div>
<br>

<div name="lifecycle-depen">

>  <samp> lifecycle depen </samp>

```kotlin
// ViewModel
implementation "androidx.lifecycle:lifecycle-viewmodel-ktx:2.3.1"

// LiveData
implementation "androidx.lifecycle:lifecycle-livedata-ktx:2.3.1"

// Lifecycles only (without ViewModel or LiveData)
implementation "androidx.lifecycle:lifecycle-runtime-ktx:2.3.1"

// Saved state module for ViewModel
implementation "androidx.lifecycle:lifecycle-viewmodel-savedstate:2.3.1"

// Annotation processor
kapt "androidx.lifecycle:lifecycle-compiler:2.3.1"

// alternately - if using Java8, use the following instead of lifecycle-compiler
implementation "androidx.lifecycle:lifecycle-common-java8:2.3.1"
```
</div>
<br>

<div name="navigation-depen">

>  <samp> navigation depen </samp>

```kotlin
// Navigation Component
    implementation "androidx.navigation:navigation-fragment-ktx:2.3.5"
    implementation "androidx.navigation:navigation-ui-ktx:2.3.5"
```
</div>
<br>

<div name="paging-depen">

>  <samp> paging depen </samp>

```kotlin
// Paging 3
    implementation "androidx.paging:paging-runtime-ktx:3.0.0"
```
</div>
<br>

<div name="retrofit-depen">

>  <samp> retrofit depen </samp>

```kotlin
// Retrofit
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'
    implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
    implementation "com.squareup.okhttp3:okhttp:4.9.0"
    implementation "com.squareup.okhttp3:logging-interceptor:4.5.0"
```
</div>
<br>

<div name="room-depen">

>  <samp> room depen </samp>

```kotlin
// Room
    // kapt plugin: cut it and paste in plugins
    id 'kotlin-kapt'
    
    implementation "androidx.room:room-runtime:2.3.0"
    // To use Kotlin annotation processing tool (kapt)
    kapt "androidx.room:room-compiler:2.3.0"
    // optional - Kotlin Extensions and Coroutines support for Room
    implementation "androidx.room:room-ktx:2.3.0"
```
</div>
<br>

<div name="safeargs-classpath">

>  <samp> safeargs classpath </samp>

```kotlin
classpath "androidx.navigation:navigation-safe-args-gradle-plugin:2.3.5"
```
</div>
<br>

<div name="safeargs-plugin">

>  <samp> safeargs plugin </samp>

```kotlin
id 'androidx.navigation.safeargs.kotlin'
```
</div>
<br>

<div name="view-and-data-binding">

>  <samp> view and data binding </samp>

```kotlin
buildFeatures {
    viewBinding true
    dataBinding true
}
id 'kotlin-kapt'
```
</div>
<br>

<div name="view-binding">

>  <samp> view binding </samp>

```kotlin
buildFeatures {
    viewBinding true
}
```
</div>
<br>

## How to create your own live templates? 💡
<br>

[Official documentation](https://www.jetbrains.com/help/idea/creating-and-editing-live-templates.html)

[Live template variables](https://www.jetbrains.com/help/idea/template-variables.html)
<br>

## Suggest me
<br>
<samp> If you have any suggestion or you want to add any other templates than ping me on </samp> <a href="https://www.instagram.com/code.fun/"><img src="https://img.shields.io/badge/Follow-%40code.fun-red?style=social&logo=instagram" alt="Instagram Badge"/></a>
<br>

## Contribute
<samp> Contributions are always welcome!😇 </samp>
Please read the [contribution guidelines](contributing.md) first.
