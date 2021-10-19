
## Ninja Gold

**Project description:** This project was one of the first mini games that I created while attending Coding Dojo. It allows the user to earn gold by visiting a Farm, Cave, House, or Casino. Each location gives a different amount of gold and adds that amount to the users total. The locations also all have a unique range of gold that could be earned. Users can actually lose gold or win big if they decide to pick the Casino.

### Logic used to create game.

```python
GOLD_MAP = {
    "farm": (10,20),
    "cave": (5,10),
    "house": (2,5),
    "casino": (0,50)
}

def index(request):
    if not "gold" in request.session or "activities" not in request.session:
        request.session['gold'] = 0
        request.session['activities'] = []
    return render(request, 'index.html')

def reset(request):
    request.session.clear()
    return redirect('/')

def process_gold(request):
    if request.method == 'GET':
        return redirect('/')
    building_name = request.POST['building']
    building = GOLD_MAP[building_name]
    building_name_upper = building_name[0].upper() + building_name[1:] 
    curr_gold = random.randint(building[0], building[1])
    now_formatted = datetime.now().strftime("%m/%d/%Y %I:%M%p")
    result = 'earn'
    message = f"Earned {curr_gold} from the {building_name_upper}! ({now_formatted})"

    if building_name == 'casino':
        if random.randint(0,1) > 0:
            message = f"Entered a {building_name_upper} and lost {curr_gold} golds... Ouch... ({now_formatted})"
            curr_gold = curr_gold * -1
            result = 'lose'
    request.session['gold'] += curr_gold
    request.session['activities'].append({"message": message, "result": result})
    return redirect('/')
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
