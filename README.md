# Working Progress...

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
      - [Drawable]
      - XML
      - Util
      - Gradle dependency
  - How to create your own live template? 😊
  - Suggest me!  ✒️

---

## What is live template? 😮
<samp> Live Templates are code snippets that you can insert into your code by typing their abbreviation and pressing tab.
By using them, you can quickly and intelligently add frequently used code patterns and constructs to your code, letting the IDE do the tedious work for you. </samp>

## How to import all live templates in 1 minute? 💥
<img alt="How to import all live templates" src="assets/howToImport.gif"> </img>

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

### 📌 Dependency Injection
<br>

<div name="di-hilt-app">

>  <samp> di hilt app </samp>

```kotlin
