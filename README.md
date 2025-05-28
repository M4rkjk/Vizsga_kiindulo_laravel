DBForge: sql importálása
.env -> adatbázis neve
php artisan migrate 
modellek létrehozása: php artisan make:model
    - jellemzők beállítása ($primaryKey, $table, public $timestamps, $guarded)
    - kapcsolat metódusok (belongsTo, hasMany, hasOne)
controller létrehozása: php artisan make:controller DataController --api
api.php -> utvonalak letrehozasa (get-books -> getBooks)
    Route::get('/get-all-universities', [DataController::class, 'getAllUniversities']);
-DataController: 
    metódusok létrehozása


    MODELL
    protected $table = 'asteroids';
    protected $primaryKey = '_id';
    protected $guarded = [];
    public $timestamps = false;
    protected $hidden = ['_id', 'corporation_id'];


    public function stat()
    {
        $stat = DB::table('FO_TÁBLA_NEVE') // pl. space_agencies
        ->join('KAPCSOLT_TÁBLA_NEVE', 'FO_TÁBLA.PRIMARY_KULCS', '=', 'KAPCSOLT_TÁBLA.FOREIGN_KULCS')
        ->groupBy('KAPCSOLT_TÁBLA.NAME')
        ->select(
            'KAPCSOLT_TÁBLA.NAME',
            DB::raw('COUNT(*) as összeg')
        )
        ->get();

        return response()->json($stat);
    }

    $index = 1;
        foreach ($asteroids as $asteroid) {
            $asteroid['index'] = $index . '.';
            $index++;
        }
