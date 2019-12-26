# NepaliDateConverter

# It has followin methods available

  public interface IDateConverter  
    {  
        ConvertedDate GetBsDateFromAdDate(int adYear, int adMonth, int adDate);  
        DateTime GetAdDateFromBsDate(int bsYear, int bsMonth, int bsDate);  
    }  
    
# And Returns the following object

   public class ConvertedDate  
    {  
        public int Year { get; set; }  
        public int Month { get; set; }  
        public int Day { get; set; }  
    }  
    
 # TO use it, register singleton service in startup.cs as below
    services.AddSingleton<IDateConverter,DateConverter>();  
    
 # And inject IDateConverter into constructor of any class where you want to convert the date
 
  private IDateConverter _dateConverter;  
  
  public HomeController(IDateConverter dateConverter){  
    _dateConverter = dateConverter  
  }  
  
  public IActionResult Index(){  
    var bsDate = _dateConverter.GetBsDateFromAdDate(2019,09,21);  
    var bsYear = bsDate.Year;  
    var bsMonth = bsDate.Month;  
    var bsDay = bsDate.Day;  
  }  
