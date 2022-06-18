package coverage

import (
	"os"
	"reflect"
	"testing"
	"time"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW
func TestMatrix_Cols(t *testing.T) {
	type fields struct {
		rows int
		cols int
		data []int
	}
	tests := []struct {
		name   string
		fields fields
		want   [][]int
	}{
		{
			"cols test",
			fields{
				rows: 1,
				cols: 1,
				data: []int{1},
			},
			[][]int{{1}},
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			m := Matrix{
				rows: tt.fields.rows,
				cols: tt.fields.cols,
				data: tt.fields.data,
			}
			if got := m.Cols(); !reflect.DeepEqual(got, tt.want) {
				t.Errorf("Cols() = %v, want %v", got, tt.want)
			}
		})
	}
}

func TestMatrix_Rows(t *testing.T) {
	type fields struct {
		rows int
		cols int
		data []int
	}
	tests := []struct {
		name   string
		fields fields
		want   [][]int
	}{
		{
			"rows test",
			fields{
				rows: 1,
				cols: 1,
				data: []int{1},
			},
			[][]int{{1}},
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			m := Matrix{
				rows: tt.fields.rows,
				cols: tt.fields.cols,
				data: tt.fields.data,
			}
			if got := m.Rows(); !reflect.DeepEqual(got, tt.want) {
				t.Errorf("Rows() = %v, want %v", got, tt.want)
			}
		})
	}
}

func TestMatrix_Set(t *testing.T) {
	type fields struct {
		rows int
		cols int
		data []int
	}
	type args struct {
		row   int
		col   int
		value int
	}
	tests := []struct {
		name   string
		fields fields
		args   args
		want   bool
	}{
		{
			"set test",
			fields{
				rows: 0,
				cols: 0,
				data: nil,
			},
			args{
				row:   0,
				col:   0,
				value: 0,
			},
			false,
		},
		{
			"set test",
			fields{
				rows: 1,
				cols: 1,
				data: []int{1},
			},
			args{
				row:   0,
				col:   0,
				value: 2,
			},
			true,
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			m := &Matrix{
				rows: tt.fields.rows,
				cols: tt.fields.cols,
				data: tt.fields.data,
			}
			if got := m.Set(tt.args.row, tt.args.col, tt.args.value); got != tt.want {
				t.Errorf("Set() = %v, want %v", got, tt.want)
			}
		})
	}
}

func TestNew(t *testing.T) {
	type args struct {
		str string
	}
	tests := []struct {
		name    string
		args    args
		want    *Matrix
		wantErr bool
	}{
		{"create matrix test",
			args{str: "123\n3210"},
			&Matrix{rows: 2, cols: 1, data: []int{123, 3210}},
			false,
		},
		{
			"create matrix test fails because string",
			args{str: "s"},
			nil,
			true,
		},
		{
			"create matrix test fails because matrix cols",
			args{str: "1 1\n1 1 1 1 1"},
			nil,
			true,
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			got, err := New(tt.args.str)
			if (err != nil) != tt.wantErr {
				t.Errorf("New() error = %v, wantErr %v", err, tt.wantErr)
				return
			}
			if !reflect.DeepEqual(got, tt.want) {
				t.Errorf("New() got = %v, want %v", got, tt.want)
			}
		})
	}
}

func TestPeople_Len(t *testing.T) {
	tests := []struct {
		name string
		p    People
		want int
	}{
		{
			"len test",
			People{},
			0,
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			if got := tt.p.Len(); got != tt.want {
				t.Errorf("Len() = %v, want %v", got, tt.want)
			}
		})
	}
}

func TestPeople_Less(t *testing.T) {
	type args struct {
		i int
		j int
	}
	tests := []struct {
		name string
		p    People
		args args
		want bool
	}{
		{
			"less test by surnames",
			People{
				Person{
					birthDay: time.Time{},
				},
				Person{
					birthDay: time.Time{}.Add(1),
				},
			},
			args{
				i: 0,
				j: 1,
			},
			false,
		},
		{
			"less test by names",
			People{
				Person{
					firstName: "1",
					birthDay:  time.Time{},
				},
				Person{
					firstName: "2",
					birthDay:  time.Time{}.Add(1),
				},
			},
			args{
				i: 0,
				j: 1,
			},
			true,
		},
		{
			"less test by birthday",
			People{
				Person{
					birthDay: time.Time{},
				},
				Person{
					birthDay: time.Time{}.AddDate(1, 2, 3),
				},
			},
			args{
				i: 0,
				j: 1,
			},
			false,
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			if got := tt.p.Less(tt.args.i, tt.args.j); got != tt.want {
				t.Errorf("Less() = %v, want %v", got, tt.want)
			}
		})
	}
}

func TestPeople_Swap(t *testing.T) {
	type args struct {
		i int
		j int
	}
	tests := []struct {
		name string
		p    People
		args args
	}{
		{
			"swap test",
			People{
				Person{
					firstName: "1",
					lastName:  "1",
					birthDay:  time.Time{},
				},
				Person{
					firstName: "2",
					lastName:  "2",
					birthDay:  time.Time{},
				},
			},
			args{
				i: 0,
				j: 1,
			},
		},
	}
	for _, tt := range tests {
		t.Run(tt.name, func(t *testing.T) {
			tt.p.Swap(tt.args.i, tt.args.j)
		})
	}
}
