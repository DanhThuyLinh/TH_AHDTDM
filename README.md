from ._anvil_designer import Form1Template
from anvil import *
import anvil.server


def merge_sort(arr):
  if len(arr) > 1:
    mid = len(arr) // 2
    L = arr[:mid]
    R = arr[mid:]

    merge_sort(L)
    merge_sort(R)

    i = j = k = 0

    while i < len(L) and j < len(R):
      if L[i] < R[j]:
        arr[k] = L[i]
        i += 1
      else:
        arr[k] = R[j]
        j += 1
      k += 1

    while i < len(L):
      arr[k] = L[i]
      i += 1
      k += 1

    while j < len(R):
      arr[k] = R[j]
      j += 1
      k += 1


class Form1(Form1Template):
  def __init__(self, **properties):
    # Set Form properties and Data Bindings.
    self.init_components(**properties)

    # Any code you write here will run before the form opens.

  def button1_click(self):
    # Đọc giá trị n từ Textbox1
    n = int(self.textbox1.text)

    # Tạo dãy số ban đầu
    data = []
    for i in range(n):
      data.append(random.randint(1, 100))

    # Hiển thị dãy số ban đầu trong Textbox2
    self.textbox2.text = str(data)

  def button_1_click(self, **event_args):
    """This method is called when the button is clicked"""
    # Lấy dữ liệu từ text_box_1
    input_data = self.nhap_vao_day_so_nguyen.text

    # Chuyển đổi dữ liệu thành mảng số nguyên
    numbers = list(map(int, input_data.split()))

    # Sắp xếp mảng số nguyên bằng thuật toán Insertion Sort
    for i in range(1, len(numbers)):
      key = numbers[i]
      j = i - 1
      while j >= 0 and numbers[j] > key:
        numbers[j + 1] = numbers[j]
        j -= 1
      numbers[j + 1] = key

    # Hiển thị kết quả đã sắp xếp trong text_box_2
    self.text_box_2.text = " ".join(map(str, numbers))

  def button_2_click(self, **event_args):
    """This method is called when the button is clicked"""
    # Lấy dữ liệu từ text_box_1
    input_data = self.nhap_vao_day_so_nguyen.text

    # Chuyển đổi dữ liệu thành mảng số nguyên
    numbers = list(map(int, input_data.split()))

    # Sắp xếp mảng số nguyên bằng thuật toán Selection Sort
    n = len(numbers)
    for i in range(n):
      min_idx = i
      for j in range(i + 1, n):
        if numbers[j] < numbers[min_idx]:
          min_idx = j
      numbers[i], numbers[min_idx] = numbers[min_idx], numbers[i]

    # Hiển thị kết quả đã sắp xếp trong text_box_2
    self.text_box_2.text = " ".join(map(str, numbers))

  def button_3_click(self, **event_args):
    """This method is called when the button is clicked"""
    # Lấy dữ liệu từ text_box_1
    input_data = self.nhap_vao_day_so_nguyen.text

    # Chuyển đổi dữ liệu thành mảng số nguyên
    numbers = list(map(int, input_data.split()))

    # Sắp xếp mảng số nguyên bằng thuật toán Bubble Sort
    n = len(numbers)
    for i in range(n):
      for j in range(0, n - i - 1):
        if numbers[j] > numbers[j + 1]:
          numbers[j], numbers[j + 1] = numbers[j + 1], numbers[j]

    # Hiển thị kết quả đã sắp xếp trong text_box_2
    self.text_box_2.text = " ".join(map(str, numbers))

  def button_4_click(self, **event_args):
    """This method is called when the button is clicked"""
    # Lấy dữ liệu từ text_box_1
    input_data = self.nhap_vao_day_so_nguyen.text

    # Chuyển đổi dữ liệu thành mảng số nguyên
    numbers = list(map(int, input_data.split()))

    # Sắp xếp mảng số nguyên bằng thuật toán Merge Sort
    merge_sort(numbers)

    # Hiển thị kết quả đã sắp xếp trong text_box_2
    self.text_box_2.text = " ".join(map(str, numbers))
